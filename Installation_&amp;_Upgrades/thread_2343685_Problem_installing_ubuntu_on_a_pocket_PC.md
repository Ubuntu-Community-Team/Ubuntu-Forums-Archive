---
title: "Problem installing ubuntu on a pocket PC"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by leobat on 2016-11-18
Hello, 
my name is Leo, new on the forum.
I'm asking here because i'm just starting in linux and never learned anything about code or else.
I'll put picture of the screen, since i can't capture it, sorry for the quality, but that will help understand the problem.
So, I bought a pocket pc by the ockel brand on kickstarter a sirius B model without OS.
On their site there is a pdf guide to install Ubuntu with a usb key on the pc (link: [https://drive.google.com/file/d/0By1Li2ybwRttRVhia2xieXMxXzg/view](https://drive.google.com/file/d/0By1Li2ybwRttRVhia2xieXMxXzg/view)). The problem is that i can't find how to launch the flashing of the PC.
To resume : 
at first, the USB with the UEFI was placed in slot fs0 and not fs3 as specified in the guide. Then i followed all the steps in the guide correctly, but when entering the command ftp.efi -f BIOS-64bit.bin --rewrite, the command isn't recognize. I asked help to a friend, he told me to try "fpt" instead of "ftp" in the command. With this correction, the flashing tool display and ask me to press enter a few time, but finally an error appear because of an invalid parameter value.
Is there someone who can help me find a solution ? 

Thank you for your attention, sorry if there are mistakes, english isn't my native tongue.

---

### Post by leobat on 2016-11-18
Sorry forgot these pictures

---

### Post by oldos2er on 2016-11-18
Thread moved to *Installation & Upgrades*

---

### Post by oldfred on 2016-11-18
Your listing of files shows the correct name as fpt.efi, so instructions had typo.
And list of options uses -F not -f, which may make a difference?
And your screenshot shows two - like --, but options show one dash like -rewrite.

Computers can be particular about the slightest differences.

---

