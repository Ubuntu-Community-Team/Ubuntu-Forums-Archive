---
title: "Install 10.04, now blank screen after Grub and fsck"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheSnacks on 2010-03-28
Hello, I am running a Dell Dimension 4600 (with internal graphics). I installed Ubuntu Studio 10.04 onto a fresh ext4 partition with all the programs. After the installation, it took me back to grub and I booted into it just fine. Then about a couple hours later I shut it down. When I go to turn it back on, I get to grub, select it, and it shows a blinking cursor for a few seconds, then 2 lines, the first starting with fsck, which disappear to fast for me to read. Then my monitor goes into a no signal sleep state. It will stay like that for as long as it's on (presumably, I left it like that for 20 minutes) no matter how many times I try to boot it. Booting 9.10 from grub works fine. There shouldn't have been any changes to it after the install except for plugging in  a webcam. Even when I unplug it it still won't boot. The exact same thing happens with the recovery mode option. This is the first time I've used the ext4, so could it be a problem with that, since it's seems to quit after fsck?

Thanks, TheSnacks.

---

### Post by coolcaseley67 on 2010-03-28
hi

-no it is  not EXT 4 .

- There are bugs and issues with 10:04 as it's in development .

- i do not know of a work round but if you can get in to recovery mode choose drop root to shell( log-in if needed ) type sudo update-grub which you can not !! 

- try a fresh install this time do not install any 3thr ptty drivers !! 

- then update with back port & proposed . it will work !!

- and move this post in to the ubuntu 10:04 bit of this forum for more help .

hope it helps

---

### Post by TheSnacks on 2010-03-28
I apologize for the false alarm, but it is working now. I don't know why, but after I posted that i restarted, and seemed to do the same thing. When I went to hit the power button, it popped up with the login. This is the same thing I've been doing, so I don't know why it's working now. Probably just because I asked :D

---

### Post by theozzlives on 2010-03-28
It's doing that. The boot will screw up and you just turn it off and it works fine. Remember it's still in development. This should be Alpha 4, but they called it Beta 1 and gave it to the public for some reason.

---

### Post by coolcaseley67 on 2010-03-28
Hi theozzlives

- agreed , there lot and lots of bugs , you fine at last  2
 max every week in a good beta , but no  beta 1in  i keep on finding bugs  every day i use it !and nobody appears to be fixing them :o

---

### Post by sgosnell on 2010-03-28
The bugs are being fixed.  It just takes some time, but every update fixes more of them.

My boot hangs at a blank screen for ~25 seconds or so, then the rest of the boot goes quickly.  There are issues with plymouth, and there is a very long thread on that subject in the Lucid testing forum.  The only reason for using 10.04 right now is for testing it.  That's what betas are for, to let users find the bugs that remain.  Never, ever run a beta version of anything on a machine you rely on for everyday use.

---

### Post by Sef on 2010-03-28
Moved to Lucid.

---

