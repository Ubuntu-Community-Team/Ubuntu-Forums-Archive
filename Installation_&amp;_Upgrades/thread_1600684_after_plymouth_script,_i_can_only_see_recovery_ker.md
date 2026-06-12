---
title: "after plymouth script, i can only see recovery kernels in GRUB2"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by musikele on 2010-10-19
Hello Everybody. 
I am using a Dell XPS m1330 with ubuntu Maverick 10.10 and with a Nvidia card. 
Recently I wanted to add plymouth support to my boot screens via this script: [http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/](http://kyleabaker.com/2010/07/11/how-to-fix-your-ubuntu-boot-screen/) 
but maybe i did something that ruined my pc and now, in GRUB, i can only see recovery kernels.
The situation is this: in grub i see 

linux recovery kernel 1
linux recovery kernel 2 (old one) 
memtest
windows 7 

My "normal" linux kernels disappeared. 
When I want to boot linux I use a recovery kernel, then I simply hit "resume" in the process, do the textual login and than use the command "startx" to start the system. However i'm getting no Plymouth and no normal boot.

I have already tried to fix grub recreating the linux kernels, but they just don't show.

Any ideas? 
p.s. nvidia drivers are correctly installed, as I can use compiz normally. 

Thanks to all! 
Michele

---

### Post by musikele on 2010-10-19
Hi, I resolved the problem.
In my case, instead of running the script, I did the steps one-by-one, as contained in a post linked to the page. I found that i introduced some errors in some config files, and now that everything looks good, grub compiled and returned me the standard kernels - as well as plymouth. 
What else.. if you get, at the end, an error when you do "update-initramfs -u", unistall the canonical-census packet. As far as I know, it blocks this operation. Bye!

---

