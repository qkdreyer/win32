---
description: CTransInPlaceFilter.DecideBufferSize method - The DecideBufferSize method sets the output pin's buffer requirements.
ms.assetid: f1ddc39e-dcd5-4a44-8a8e-e384692408e1
title: CTransInPlaceFilter.DecideBufferSize method (Transip.h)
ms.topic: reference
ms.date: 4/26/2023
topic_type: 
- APIRef
- kbSyntax
api_name: 
- CTransInPlaceFilter.DecideBufferSize
api_type: 
- COM
api_location: 
- Strmbase.lib
- Strmbase.dll
- Strmbasd.lib
- Strmbasd.dll
ms.custom: UpdateFrequency5
---

# CTransInPlaceFilter.DecideBufferSize method

\[The feature associated with this page, [DirectShow](/windows/win32/directshow/directshow), is a legacy feature. It has been superseded by [MediaPlayer](/uwp/api/Windows.Media.Playback.MediaPlayer) and [IMFMediaEngine](/windows/win32/api/mfmediaengine/nn-mfmediaengine-imfmediaengine). **MediaPlayer** and **IMFMediaEngine** have been optimized for Windows 10 and Windows 11. Microsoft strongly recommends that new code use **MediaPlayer** and **IMFMediaEngine** instead of **DirectShow**, when possible. Microsoft suggests that existing code that uses the legacy APIs be rewritten to use the new APIs if possible.\]

The `DecideBufferSize` method sets the output pin's buffer requirements.

## Syntax


```C++
HRESULT DecideBufferSize(
   IMemAllocator        *pAlloc,
   ALLOCATOR_PROPERTIES *pProperties
);
```



## Parameters

<dl> <dt>

*pAlloc* 
</dt> <dd>

Pointer to the [**IMemAllocator**](/windows/desktop/api/Strmif/nn-strmif-imemallocator) object used by the output pin.

</dd> <dt>

*pProperties* 
</dt> <dd>

Pointer to the requested allocator properties for count, size, and alignment, as specified by the [**ALLOCATOR\_PROPERTIES**](/windows/win32/api/strmif/ns-strmif-allocator_properties) structure.

</dd> </dl>

## Return value

Returns an **HRESULT** value. Possible values include those shown in the following table.



| Return code                                                                            | Description        |
|----------------------------------------------------------------------------------------|--------------------|
| <dl> <dt>**S\_OK**</dt> </dl>   | Success<br/> |
| <dl> <dt>**E\_FAIL**</dt> </dl> | Failure<br/> |



 

## Remarks

This method is called when the **CTransInPlaceFilter** class needs to provide a buffer size to the downstream filter. If the **CTransInPlaceFilter** filter is already connected upstream, it uses the allocator properties on the upstream pin connection. Otherwise, it sets the buffer size to 1 byte as a temporary place-holder value. When the upstream filter connects, the **CTransInPlaceFilter** class renegotiates the downstream allocator. For more information about the pin connection process in this class, see [**CTransInPlaceFilter Class**](ctransinplacefilter.md).

## Requirements



| Requirement | Value |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Header<br/>  | <dl> <dt>Transip.h (include Streams.h)</dt> </dl>                                                                                   |
| Library<br/> | <dl> <dt>Strmbase.lib (retail builds); </dt> <dt>Strmbasd.lib (debug builds)</dt> </dl> |



## See also

<dl> <dt>

[**CTransInPlaceFilter Class**](ctransinplacefilter.md)
</dt> </dl>

 

 




