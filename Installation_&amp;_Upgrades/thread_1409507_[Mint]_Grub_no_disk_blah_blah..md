---
title: "[Mint] Grub no disk blah blah."
date: 2010-02-17
forum: Installation &amp; Upgrades
---

### Post by falkflyer on 2010-02-17
Hello all,
  I recently decided to take an unused 4GB flash drive and dump Linux Mint on it, since I've never used Linux before and this one comes recomended.
  Anyway, I have no experience with Linux as mentioned, so I guess the odds are that the installation would go well, but then my Vista (I know, I know, but I have yet to get a copy of 7) would break.  I'm not too worried, as I see this is a common issue.
  During the installation, I was told that some partitions could not be used because they were mounted, and if I wanted to repartition them I would have to unmount them, is that the issue?  I'm guessing that it unmounted my Vista partition and recovery partition during the installation, but then again, what do I know?
  Anyway, help would be very appreciated.  I got my LiveCD to boot up, so I guess I can use that for the time being.

---

### Post by darkod on 2010-02-17
I don't know the install process of Mint but I didn't understand anything. :)
Do you expect the Mint install to break your vista? Why?
Also, the message about mounted partitions doesn't make any sense, especially if you are wiping the whole usb stick during install so you can use it as destination. Is that what you want?

---

### Post by oneindelijk on 2010-02-17
Mint should give you install options (like erasing windows Vista or Dual booting), but from a USB stick that shouldn't be an issue at all.
Can you tell us more precisely where you're stuck ?

---

### Post by falkflyer on 2010-02-17
Alright, here's how it happened.
I popped in my Mint CD and booted up.  Did "Install Mint 8" and walked through the process.  It got to a part where it asks where I want to install it - I chose to erase everything on my memory stick and install it there.  After the process, I checked my main hard drive to ensure Winows was still there - it was, along with all of my other files.  Mint didn't seem to touch my internal hard drive.
The problem is that now when I boot, I get the GRUB error message about "no disk".  So far, I have only been able to boot up with the LiveCD successfully.

---

### Post by nigrunze on 2010-02-17
Try booting without your USB stick in the computer, then with it in your computer. If GRUB loads only when your USB stick is plugged in, then chances are that you installed GRUB to the Master Boot Record of your hard drive instead of your USB stick. The rest of the GRUB bootloader should be on your USB stick regardless.

If that turns out to be the case, hopefully you have either a Windows Vista DVD or a Windows Vista recovery disc that you downloaded from somewhere.

---

### Post by darkod on 2010-02-17
> **nigrunze said:**
> Try booting without your USB stick in the computer, then with it in your computer. If GRUB loads only when your USB stick is plugged in, then chances are that you installed GRUB to the Master Boot Record of your hard drive instead of your USB stick. The rest of the GRUB bootloader should be on your USB stick regardless.

If that turns out to be the case, hopefully you have either a Windows Vista DVD or a Windows Vista recovery disc that you downloaded from somewhere.

+1

You didn't mention whether you checked where grub will go. For multiple drives (even if that's multiple internal hdds) you always need to check where the bootloader will go. Never assume. :)

Even if you don't have vista/7 DVD, you can install generic windows mbr from ubuntu (I guess also from mint) with (assuming your internal hdd is /dev/sda):

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Then install grub on the MBR of the stick and you're good to go.

PS. Have you checked whether your computer can boot from USB?

---

### Post by falkflyer on 2010-02-17
Hey gang, thanks for the helpful replies!

while you were all snickering at my badness (har har) I went on a hunch and also partitioned some of my external hardrive for a fresh install of Linux - now I can boot up into Mint, which I couldn't before, which then lets me choose which OS to boot from.  I went Vista, did some diagnostic stuff, and long story short, got it to boot up.  However, you guys appear to have nailed it - my computer now likes to boot to Mint first, so I'm booting off of an external HDD.  For now that works, unless I get some performance impacts, but so far so good.  However, I would like to be able to -not- do this, so how would I fix it?
My HDD is /dev/sba1 I believe.  darkod, how would I use your commands to do this?  Would I still use mbr and just use my HDD's actual address?

---

### Post by oneindelijk on 2010-02-17
So, basically what you have to do, from within the live cd is 
#1 Make a USB startup disk (why not Ubuntu ?)
It's in the system menu...

#2 Run the Vista Installation CD and choose the repair option
(XP has that, so I suppose so does vista)
Or you can run a command console and type fixmbr
That should restore the Vista Bootloader

(I'm not trying this as I type, so I hope it's correct)

---

### Post by nigrunze on 2010-02-17
> **oneindelijk said:**
> 
#2 Run the Vista Installation CD and choose the repair option
(XP has that, so I suppose so does vista)
Or you can run a command console and type fixmbr
That should restore the Vista Bootloader
With Windows Vista and Windows 7, it's a little bit different.

Start your computer with the Windows Vista disc. Choose your language(s), etc. On the next screen, you'll see a huge "Install Now" button, but instead click the "Repair" link in the bottom left corner.

I might be off by a little bit with the next step.

If it finds a problem at first glance, it'll offer to fix it, but you can choose to skip that. Click "Command Prompt". Now, making sure that you have the correct drive selected, type "bootrec /fixmbr".

You're done. Restart.

---

### Post by falkflyer on 2010-02-17
Alright, so I have no recovery disc, but there is a recovery drive.  I got to the command prompt, but I can't switch off of X:\ to C:\.  Are they the same?

---

### Post by nigrunze on 2010-02-17
> **falkflyer said:**
> Alright, so I have no recovery disc, but there is a recovery drive.  I got to the command prompt, but I can't switch off of X:\ to C:\.  Are they the same?

To change drives, type "c:" . To list the directory contents, type "dir". To change directories, type "cd xx", same as in linux.

---

### Post by falkflyer on 2010-02-17
Haha, thanks.  I was trying to cd C:\, silly me.

---

### Post by darkod on 2010-02-18
/dev/sda1 is a partition, not hdd. If it has a number it's a partition on the particular hdd. If you meant to say vista is on /dev/sda1 which is to be expected, then the hdd is /dev/sda. Yes, you should run them as I wrote them:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Note that they work on ubuntu but I haven't tried them on mint. Ignore any warnings that you'll probably get, it's normal.

---

