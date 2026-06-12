---
title: "Install From USB without Windows"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by JVP3122 on 2011-04-14
I apologize if this has been asked before, but I couldn't find anything with my specific problem.  The place on my hard drive Windows is found is corrupt, and I'm trying to install Ubuntu as the only OS.  I tried putting the 10.10 .iso on my USB and booting from that drive, but for some reason it keeps trying to go to Windows.  It's almost like my computer doesn't recognize that the USB is there.  I followed the instructions on this site [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) for creating the bootable image on my USB using Windows because I'm on my wife's computer.  I've tried changing the boot order on my computer, but it still keeps going over the USB to booting from the HDD.  Posting here is my last resort before I go and buy another hard drive.

---

### Post by Dutch70 on 2011-04-14
Hi and wecome to UF

Is your usb stick formatted to FAT32?
You may also want to try Unetbootin to create the usb stick.
[[COLOR="Red"]http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/[/COLOR]]("http://www.pendrivelinux.com/using-unetbootin-to-create-a-live-usb-linux/")

I would also check the md5sum of the downloaded .iso. 
[[COLOR="Red"]https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM%20on%20Windows")

Can you not hit the escape key to bring up your boot options and then choose the usb stick? 

I certainly wouldn't be in a hurry to go buy a new hard drive. It won't have anything to do with booting from the usb stick.

---

### Post by kn0w-b1nary on 2011-04-14
+1 to UNetbootin. I would recommend downloading the .iso manually instead of letting UNetbootin doing it for you.

---

### Post by JVP3122 on 2011-04-14
Thanks for the help.  I tried using that program to burn the bootable USB and it still didn't help with the boot.  I'm wondering if it's the Ubuntu .iso that I downloaded.  I downloaded the 64 bit 10.10 because that's what my computer is.  The thing is, though, that I noticed in the file name that it mentions amd.  I'm not sure if it matters that my chipset is an Intel i7, though.  Thanks for the help so far, I really appreciate it.

Also, yes, I went into the boot menu (F2 on my computer) and moved the USB to the top of the boot list.

---

### Post by kn0w-b1nary on 2011-04-14
the amd64 works on intel x64, as well as i386 on amd.

---

### Post by JVP3122 on 2011-04-14
> **kn0w-b1nary said:**
> the amd64 works on intel x64, as well as i386 on amd.

Any suggestions as to what I might need to try and do?  The md5 Hash numbers are the same, I've used UNetbootin to create the image on a properly formatted USB stick, and I've changed the boot order to start with the USB drive, and for some reason it's still not recognizing it.

---

### Post by Dutch70 on 2011-04-14
Just a thought, are you're usb ports2.0 or 3.0? 
Try different usb ports on your computer...all of them.

---

### Post by JVP3122 on 2011-04-14
Almost positive they're all 2.0. I've got three and I've tried installing from each of them.
I'm thinking about trying to burn the disc instead hoping that might make a difference.

---

### Post by kn0w-b1nary on 2011-04-14
Try [this.](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by Dutch70 on 2011-04-14
You may also want to try 10.04 which is the current LTS (long term support) version and not much different than 10.10. 

10.10 is known to have a bug with some usb sticks. If you've got a different one, you may want to try that.

You do have it formatted to FAT32, and you've tried hitting the escape key while booting, right?

---

### Post by JVP3122 on 2011-04-14
I've tried hitting ESC, which doesn't do anything.  I think on my computer it's the F2 key.  I'm going to try 10.04 and what kn0w-b1nary suggested.  Hopefully one of them works.  I'll let you know if they do, in case you're curious.  Thanks for the help, folks.

---

### Post by kn0w-b1nary on 2011-04-14
Glad to help! ;)

---

### Post by wilee-nilee on 2011-04-14
There is a seperate per session boot menu key prompt just like the f2 for the bios menu that you can change. On my computer it is f12, this is the problem will would wager, look for a per session boot with your computer model on google if you can't figure it out, or the manual. It could be any one of the f keys or delete ....etc.

---

### Post by JVP3122 on 2011-04-16
Just in case you guys are curious, I had to burn the .iso to a DVD and install it that way.  For some reason my computer wasn't reading the usb drive properly.  Everything worked well, and I've been amazed at just how much faster this OS is than my previous one.  Thanks again for all of your help, everybody!

---

### Post by Dutch70 on 2011-04-16
Great! Glad you got it going. :)

So, is this thread [Solved]?

---

### Post by kn0w-b1nary on 2011-04-16
Glad you got it working! :D

---

