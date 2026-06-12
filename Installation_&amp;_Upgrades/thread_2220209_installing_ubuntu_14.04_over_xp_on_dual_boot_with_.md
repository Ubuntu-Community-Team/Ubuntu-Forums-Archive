---
title: "installing ubuntu 14.04 over xp on dual boot with mint"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by darryl2 on 2014-04-27
I am trying to install ubuntu in the parition space current used by xp. I also have mint 13 which I wish to keep.
My current drive lay out is sda(ntfs) 60gb - xp  sda5(ext4) 17.8gb - mint & sda6(swap). I would prefer the size of the mint parition to be bigger i.e half the drive space.
When I try to install ubuntu it  only gives me the option to install over the top of mint. It does allow me to resize paritions though.
So I select the "something else" option. It allows me to resize xp partion but not mint, so I'd end up with 3 paritions, not including swap.
Anyway i thought Id install over xp and worry about resizing for another day as I store everything on an external drive so the size of the mint parition was not a huge concern.
So I highlighted the xp parition and selected it from the drop down box at bottom of screen click next and get "no root file system is defined" message.
So I'm not sure what I'm suppose to do as there are no options on the  parition screen. Should I use gparted before to resize paritions, do I need to delete xp and reformat that parition before installation?
Thanks for any help.

---

### Post by fantab on 2014-04-27
When Installaing Ubuntu, at the 'Installation Type' dialog choose 'Something Else'... 
Select the partition you want to install Ubuntu to and set it up as follows:
use as: ext4 journaling system
mountpoint: /
format: yes

Thats it... continue with installation.

---

