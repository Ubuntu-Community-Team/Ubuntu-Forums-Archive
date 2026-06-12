---
title: "Help Installing Ubuntu in Thinknote Green320 Laptop"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by sub_zer0 on 2008-07-21
I have an old laptop,ECS Thinknote Green320, 1Ghz Processor, 256MB Ram, with 16Mb set shared Graphics Memory (Via CLE266).

I was trying to install ubuntu on this and it always freezes after this screen, right after selecting the "Install Ubuntu"
[IMG]http://bp2.blogger.com/_XstHr5uAQXk/Rl1TCoDV-hI/AAAAAAAAAAc/c0IuTSpFpFI/s320/Ubuntu+Load.png[/IMG]
And the screen acts like it was turned off.
The CD works fine "Ubuntu 8.04 i386"
I would really appreciate your help. Thanks in advance!

---

### Post by PmDematagoda on 2008-07-21
With the specifications you have, perhaps Ubuntu may be a bit much which may cause the problem you are facing with it. Why don't you try a lighter alternative like [Xubuntu]("http://www.xubuntu.org/get") and see if it works any better?

---

### Post by sub_zer0 on 2008-07-21
Thanks! I'll download Xubuntu right now and see it if works.

---

### Post by wmartyr on 2008-07-21
I have the same laptop. It used to work fine with 7.04 and 7.10. Now I can't install 8.04 using the disc i got direct from canonical. I downloaded xubuntu 8.04 and it also freezes after completing the progress bar. I even tried OzOS which is also based on Hardy and I also get the same result. Any ideas?

---

### Post by sub_zer0 on 2008-07-21
> **wmartyr said:**
> I have the same laptop. It used to work fine with 7.04 and 7.10. Now I can't install 8.04 using the disc i got direct from canonical. I downloaded xubuntu 8.04 and it also freezes after completing the progress bar. I even tried OzOS which is also based on Hardy and I also get the same result. Any ideas?

Maybe I should have read your post earlier. And you're right, its not working either. I think the problem is hardware related. Is there any way to make ubuntu/xubuntu work on this hardware? If not, then I'm stuck on Windows XP...

---

### Post by Rui Pais on 2008-07-22
> **wmartyr said:**
> I have the same laptop. It used to work fine with 7.04 and 7.10. Now I can't install 8.04 using the disc i got direct from canonical. I downloaded xubuntu 8.04 and it also freezes after completing the progress bar. I even tried OzOS which is also based on Hardy and I also get the same result. Any ideas?

Hi
Have you try it by running 'Install' from boot menu or from the living session? 
The first approach it's known to have problem with several Ubuntu derivatives, OzOS included.

---

### Post by snowpine on 2008-07-22
The Ubuntu LiveCD now requires 384mb ram. However, you can download the Alternate CD, which uses a text-based installer and should install with 256mb.

Xubuntu is a good choice too. :)

---

### Post by JLF65 on 2008-12-27
I've run into the same problem with an ECS Green 320 laptop. I've got it maxed out at 512MB of RAM, so it's not a RAM problem. When you hit the point where the laptop video goes away, I connected an external monitor... and there's video there. It seems that the driver no longer does mirroring to both video heads by default since 8.04. Trying it with the external monitor from the start shows the same video to the LCD and ext monitor right up to that point where the LCD is shut off, leaving you with just video on the ext monitor.

Funny thing is, the video out from the monitor wasn't a mode my monitor could handle, so I still couldn't go any farther. I can tell there's video there, it's just all scrambled. :rolleyes:

Okay, after a bit more searching with google, I've found the problem is that the "386" kernel for Ubuntu/Xubuntu is actually compiled for 686 at a minimum. The C3 processor in these laptops don't have one of the 686 optional instructions (specifically, cmov). Because of that, the kernel bombs out right at that point. So that's what was on my monitor - a message that my processor doesn't support this kernel. Seeing how this has been a problem since 8.04 with bug reports filed with the priority set to high, I don't think they care.

---

### Post by natravis on 2009-01-11
I'm also trying to install Ubuntu onto a similar laptop with the same results. I originally planned to install Xubuntu w/ lame results as seen above. I upgraded it to 1GB of ram so I'm unsure why Ubuntu wasn't working pretty much right away, but I'm going to try a few more tricks and see if that fixes it. I'll update with results.

---

