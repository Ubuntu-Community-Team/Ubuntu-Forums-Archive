---
title: "Problem with avcodec_find_encoder_by_name()"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by khssibi-sabri on 2014-05-13
hi,
I have installed FFMPEG with opus codec. when i try this code:
[PHP]pCodecEncoder = avcodec_find_encoder_by_name("libopus");
    if (pCodecEncoder == NULL)
        error("Codec libopus not found!");
[/PHP]

I can't found the codec. How i can resolve this problem thank you

---

