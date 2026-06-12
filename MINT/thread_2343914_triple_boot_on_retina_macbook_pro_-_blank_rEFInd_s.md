---
title: "triple boot on retina macbook pro - blank rEFInd screen"
date: 2016-11-20
forum: MINT
---

### Post by stevesbh77 on 2016-11-20
Hello All,

Apologies for this type of question, mainly because I've seen a lot of them out there and yet I have not been able to utilize any of them. 

I have a retina MBP with OS X El Capitan (10.11.6) on a 15" Mid 2014 laptop. I basically, long ago, followed [http://davidlively.com/notes/macbook-pro-triple-boot/](http://davidlively.com/notes/macbook-pro-triple-boot/) and it has been working for a long time. 

I think I screwed it up though when I installed fuse-ext2 - I'm not blaming that project, maybe I did something, but at any rate, now when it starts I only get a dimly lit black screen. I have to hold down Option key and the I only get 3 icons: OS X, OS X, and WINDOWS. The middle one "doesn't work" it just sits there. Windows used to work but not it complains of not being able to start. From Mac (the first one), El Capitan works fine and I can see the contents of the Windows partition (it was made with Bootcamp).

Here is some info about my layout of the SSD:

sbhs-MBP:Volumes sbh$ diskutil list
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *1.0 TB     disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:       Microsoft Basic Data BOOTCAMP                200.8 GB   disk0s2
   3:                  Apple_HFS DATA                    272.9 GB   disk0s3
   4:                  Apple_HFS OS X                    249.5 GB   disk0s4
   5:                 Apple_Boot Recovery HD             650.0 MB   disk0s5
   6:                 Linux Swap                         20.0 GB    disk0s6
   7:       Microsoft Basic Data                         215.3 GB   disk0s7
   8:           Linux Filesystem                         40.7 GB    disk0s8

Btw, #3 is just a shared partition with data on it - no OS; 7 & 8 are linux mint 17.3 and 18

If I use a live mint stick I can see everything on disk0s7 and disk0s8, and think they are probably okay. It seems to be a booting issue. 

Most recently I have re-blessed rEFInd on the EFI partition (/dev/disk0s1) and yet I still get a dimly lit black screen...  Currently though I am writing this on the El Capitan (disk0s4)

I am at a loss as to how to get all these boot issues fixed. Thank you all much for your help and advice,

Brett

---

### Post by g33zr on 2016-11-20
When you set up your boot/efi partition, did you check the esp flag?

---

### Post by stevesbh77 on 2016-11-20
Hhhmmmmmm... I honestly do not remember that long ago... I just remember setting the bootloader to "/".... All I can say is that both LM 17.3 & LM 18 worked fine, until I screwed it up ;)

---

### Post by QIII on 2016-11-20
Hello!

Moved to MINT.  Note that Apple Hardware Users is a sub-forum of Ubuntu Specialised Support.  Mint is not Ubuntu.

You should still expect good support here.

---

### Post by stevesbh77 on 2016-11-20
whoops! sorry

---

### Post by QIII on 2016-11-20
No problem.  There are a lot of Mint users on the forums, so you yould be OK.

---

### Post by stevesbh77 on 2016-11-21
Well all, I know there might not have been a lot of information on this case but I'm going to say what I did and its (successful) outcome anyway - maybe it will give someone an idea as to how to fix their similar problem.

So with basically just a working OS X on /dev/sda4 (recovery on /dev/sda5), I reinstalled Win 10 from the BootCamp-made USB drive (the standard way of doing it I guess). I let it finish and install all the drivers and reboot. Then my laptop only would start up in Win10. Using the Option key I could pick OS X though.  I then, using a LM18 USB, followed [https://community.linuxmint.com/tutorial/view/2283](https://community.linuxmint.com/tutorial/view/2283) and did "Section 2" on reinstalling grub. I, as I did when I first followed "David Lively" in the link above, made sure to install it on /dev/sda9. (It would have been sda8 but when I reinstalled Win10 I got a new partition afterwards. I don't know what it is, nor care ha ha, but everything works so I'm not going to fix it by breaking it :D

After grub was reinstalled, I could then restart using Option key and still only saw OS X, OS X, and WINDOWS. I didn't try the 2nd OS X as it always failed (still don't know about it), but booting into OS X I then re-blessed rEFInd and rebooted. Then I saw a ton of options on my rEFInd list. Four of them work: Windows 10, OS X, LM17.3 and LM18. I did not try any of the others (things like "Legacy...." and Recoveries). I may try the OS X recovery but I don't feel like pushing right now.

So basically reinstalling GRUB on top of / seemed to do it, and then re-blessing rEFInd from OS X.

Good luck to all.

---

