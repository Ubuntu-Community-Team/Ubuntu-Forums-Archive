---
title: "Update Grub1.98 after Cloning a partition using 'dd'"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by just_ken_here on 2011-10-24
hi.

I cloned an exact partition of SDA2 into SDA4 using dd command.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

The clone works!! It was easy..

But now, I want the grub menu to also list my new SDA4 partition of the linux and be able to boot from there.

Doing a update-grub2 does not work.
I believe there is some things I need to add at /etc/grub.d/
I am not sure.

What is a good way to do this ?
Thanks.

---

### Post by raja.genupula on 2011-10-24
> **just_ken_here said:**
> hi.

I cloned an exact partition of SDA2 into SDA4 using dd command.
[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

The clone works!! It was easy..

But now, I want the grub menu to also list my new SDA4 partition of the linux and be able to boot from there.

Doing a update-grub2 does not work.
I believe there is some things I need to add at /etc/grub.d/
I am not sure.

What is a good way to do this ?
Thanks.

hi do this 
open your terminal 
and 
```
sudo dpkg-reconfigure grub-pc
```
while doing configure it will ask you to where you wanna install the grub.

install the grub to your sda 4

All the best.

---

### Post by just_ken_here on 2011-10-25
Thanks for the command.

I did the command.
It shows the grub 'Package Configuration' menu I suppose.. with the blue screen.

1st it prompts for 'Linux command line': 
<blank>
2nd prompts for 'Linux default command line:'
quiet splash

3rd prompt about which to install grub:
[*] dev/SDA
[ ] - dev/SDA4

I have tried 3 out of 4 combo for selection. Leaving out all blanks.

All still do not produce the SDA4 selection on boot menu..
I used '$ df ' to check the partition.
I am still booting SDA2 from the 1st boot option that just list the kernel version

What did I miss ?

Thanks

---

### Post by raja.genupula on 2011-10-25
ok use grub customizer to do that 

you can get from this link

[http://linuxtree.blogspot.com/2010/10/how-to-install-grub-customizergrub2.html](http://linuxtree.blogspot.com/2010/10/how-to-install-grub-customizergrub2.html) 

in that you can add menu entries also .

all the best,

---

