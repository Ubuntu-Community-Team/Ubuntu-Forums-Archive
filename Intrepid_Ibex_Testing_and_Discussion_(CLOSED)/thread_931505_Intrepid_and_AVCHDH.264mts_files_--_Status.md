---
title: "Intrepid and AVCHD/H.264/mts files -- Status?"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by HalNineThousand on 2008-09-27
I've tried to find this out with Google, but haven't gotten a clear answer.

I know there are problems on Gutsy with AVCHD and .mts files and that there are no programs that play back using H.264.  I understand it's the same under Hardy.

What is the status of these formats in Intrepid?  If I wait until Intrepid comes out, will I be able to play back the HD video from my camcorder on anything on Intrepid?  Will any programs let me edit it without converting it to AVI?

Is this just a matter of patching a few libraries to include it for most programs, or do all the viewing and editing programs need to be patched separately?

I know I can convert to AVI with m2tstoavi, but when I've done that, following the steps somewhere in this forum, the video was pathetically poor quality (even worse than YouTube), the 16:9 image was compressed to 4:3, which distorted everything, and there was no sound.

I have some videos, including a good one of me doing a solid tango performance for a showcase that were shot with an HD camcorder that I can't edit or trim or upload to YouTube because of these issues.

Thanks for any update on what to expect in Intrepid!

---

### Post by jtappin on 2008-09-29
> **HalNineThousand said:**
> 
I know I can convert to AVI with m2tstoavi, but when I've done that, following the steps somewhere in this forum, the video was pathetically poor quality (even worse than YouTube), the 16:9 image was compressed to 4:3, which distorted everything, and there was no sound.



Not really an answer to the main question, but certainly 2 of the above problems can be fixed by editing the ffmpeg call in the m2tstoavi script.

You can specify an explicit aspect ratio (e.g. -aspect 16:9).

The sound can be fixed by choosing an explicit audio codec instead of the default value of copy (e.g. -acodec mp3).

---

