---
title: "Grub2 update"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by rodst on 2010-01-02
I'm new to Ubuntu so please bear with me. Have installed Ubuntu (9.10 with Grub2) on 2nd HDD leaving XP on primary HDD so that I can do some testing/evaluating. I want to modify my Grub file so that my system boots into XP by default rather than Ubuntu. Currently there are 5 loading options with a line stating "GRUB_DEFAULT=0". I want to change this to "GRUB_DEFAULT=4" so that the system boots into XP by default.
 
I can edit this file (in /etc/default/grub) but when I try to save it there is no option to save it. Only "save as". And when I try to "save as" Ubunto tells me that I "do not have permissions". Can someone please tell me what I am doing wrong?
 
Also, once I have editted Grub do I need to run "update-grub"? If so, how do I do this please?
 
Apologies for the basic questions.

---

### Post by sahabcse on 2010-01-02
open the terminla and type below command

sudo gedit /etc/default/grub

then give your password and make changes

for update [grup]("http://ubuntulinux.co.in/fixing-grub.php")

---

### Post by rodst on 2010-01-02
Thanks sahabcse. Yes using terminal and issuing command
 
sudo gedit /etc/default/grub
 
make changes; save, then
 
followed by 
 
sudo update-grub
 
does the trick. Thanks.

---

