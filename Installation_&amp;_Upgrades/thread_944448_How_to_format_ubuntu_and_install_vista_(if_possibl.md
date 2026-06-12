---
title: "How to format ubuntu and install vista (if possible, kep linux and append vista)"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by iZZiDeltA on 2008-10-11
My new hard drive is installed with ubuntu durin initialisation

the linux ubuntu then partition the filesystem as ext3
and if now, lets say i wan to install another os, like vista to the hd, when i format it with cd, it says vista canot write to this hardrive
coz diff filesystem

any pro , teach me how to format or insatll 2nd os on tat hd tnx 

someppl advise me to do so:

1. Insert Ubuntu disc and startup computer
2. Select "Try Ubuntu without any change to your computer"
3. In the Ubuntu desktop, go to System > Administration > Partition Editor
4. Delete ext3 partition. Select one of the partition and format to NTFS
5. Quit Ubuntu
6. Insert Vista disc and startup computer for installation

but the thing is even the partition editor disable all the options
i canot delete, or format or do any operation to it, it's grey
i m root user, the superuser, i m stil newbie, learning n exploring ubuntu, so if any1 out there that can help me pls guide me tq so much

---

### Post by linux_lover69 on 2008-10-11
Are you wanting to get rid of Ubuntu and install vista? or have a duel boot with both installed?

---

### Post by iZZiDeltA on 2008-10-11
if possible i would lik to keep both os
now it's installed with ubuntu, can i add on vista to it?

---

### Post by linux_lover69 on 2008-10-11
look at this how to and see if you can it to work. Then tell me if it works or not. Then I'll try to help you from there.

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=1")

---

### Post by linux_lover69 on 2008-10-11
Oh and if you have a good enough computer you can install vista using a virtual drive.

---

### Post by iZZiDeltA on 2008-10-11
firstlyi wan to thank u for all ur sincerity and concerns

ok, i m folowin the instru and stumbled acros this

Firstly, boot into Ubuntu and go to Applications --> Accessories --> Terminal. Then, type in sudo gedit /boot/grub/menu.lst. 

but the menu.1st of my pc is empty, the file does exist there is not any content

wat do i do next?

---

### Post by totalnub on 2008-10-11
that's /boot/grub/menu.lst

(lowercase l, not the number 1)

try that :)

---

### Post by linux_lover69 on 2008-10-11
It's easiest if you copy and paste most of the commands its easier not to mess up that way. Because I looks like l or 1. its sometimes hard to tell what the letter or number is. And also totalnub is right.

---

### Post by iZZiDeltA on 2008-10-11
yes, i copy n paste exactly, and double verified, it's a 'l'
anyway tnx for ur attention on this matter

---

### Post by iZZiDeltA on 2008-10-11
can i add u, or is the any option to add buddy for this forum? mind if i add u as my 'mentor' to this new ubuntu? haha

---

### Post by linux_lover69 on 2008-10-11
Sure go ahead. I just added you.

---

### Post by mntokman on 2009-05-16
> **linux_lover69 said:**
> Oh and if you have a good enough computer you can install vista using a virtual drive.


I have a Sony Vaio laptop which came with Vista OS initally and  then I decided to install Kubuntu after 3 months of Xubuntu trial. However, I am very unhappy with Kubuntu and I want my Vista back and if possible Ubuntu 8.04 at the same time. 

I format my HD with ext3, not sure if it is the best but I did when I setup Kubuntu, and I was wondering if I can somehow reinstall my Vista. What are the best file systems if I want to have Vista and Ubuntu on same machine? 

I read about Virtual PC 2007, however the installation file is an .exe file...

Any suggestions?

---

