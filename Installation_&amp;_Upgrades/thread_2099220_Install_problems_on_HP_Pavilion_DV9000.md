---
title: "Install problems on HP Pavilion DV9000"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by nhare330 on 2012-12-28
Hey guys,

I have been searching around for a solution to this but I can't seem to find an answer. I have installed linux in a few different forms before. I'm using crunchbang currently, but have used all of the ubuntus and even arch a little bit. All that is just to say that this isn't my first time installing linux. Although, I don't think I have tried dual booting before.

So I am currently trying to install ubuntu on my mom's hp pavilion DV9000 notebook so that she'll have something user friendly and free. She has windows vista currently and it has gotten her viruses and continues to be slower and slower. My problem though is that I can't seem to get the ubuntu partition/hard drive to even show up on her computer or BIOS once it is installed. It is currently installed and I can't find it. I did a little research on changing the boot options with bcdedit too, but I can't even get root privileges on Vista command line so it won't let me do anything. It seems like their should be an easier solution than that anyway. Any ideas?

If I am missing something very basic could you at least point me to the right tutorial. All of my googling has gotten me to dead ends. Thanks!

(I have a few shots of the computer's bios screens that I can upload if you think that would help)

---

### Post by oldfred on 2012-12-29
Welcome to the forums.

Best to see exactly what is installed where you can install to your Ubuntu installer, or download a full repair ISO:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by nhare330 on 2012-12-29
> Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I tried out this program and it worked perfectly. I went into the advanced options of boot-repair and told it to boot ubuntu by default. Then I rebooted and Grub showed up with a full list of operating systems installed. Thanks for your help!

---

