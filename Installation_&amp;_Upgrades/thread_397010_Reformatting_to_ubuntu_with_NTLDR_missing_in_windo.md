---
title: "Reformatting to ubuntu with NTLDR missing in windows"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by deafchickadee on 2007-03-30
I loooove ubuntu; have no problems with it as I have my laptop dual booting to XP and Ubuntu. Fab!!

Now I have a tower that belonged to my ex-housemate; since he didn't chuck it, it's fair game. It has Windows XP home on it- teh OEM version i believe.

**_Issue:_** Booting up comes up with an error message "*NTLDR missing*", or what ever that means. I have googled a search for it and from what I gather it's a windows file that's either gone AWOL or something's corrupt.

My housemate never got the XP bootable CD, when he purchased the computer from whomever. Which means it cannot be reformatted with XP unless I go out and buy a brand new spanking XP cd- no thanks! So the obvious solution is to reformat and install ubuntu, which is great. I love playing with computers!

I still have the lovely Live CD on hand for when i used it to install it onto my darling little laptop.

Problem: 
1) How do i get the CD or DVD drive to boot up when it starts? 

Does anyone have any pointers? I know ith my laptop I need to contiously press F12 to get to the boot menu, is this the same for desktop computers?

---

### Post by deafchickadee on 2007-03-31
No one?

---

### Post by confused57 on 2007-03-31
Is there a prompt during bootup to press a certain key to enter setup?

You could try pressing the "Del" key, then maybe "F2"...if these don't work, then try some of the other "F" keys.  On one of my pc's, I have to hold down the "F2" key, on another pc "del" works.

Once you're able to enter bios setup, change the cd drive to boot before the hard drive.

---

### Post by otakumark on 2007-03-31
Confused is on the right track. You'll want to access your BIOS settings, typically by hitting either F1 or DEL just after your computer is turned on or restarted (if windows is loading, you missed it).

Once in the BIOS settings, track down your "Boot Options", "Boot Order" or "Boot Sequence" and set your boot order to Floppy 1st, CD second, and hard drive third. Now you'll be able to load from the CD if it's in the drive during startup.

If you need a new XP CD and you got your computer from a major computer manufacturer, such as HP, Compaq, Gateway (or even smaller companies such as VPR Matrix, eMachines, etc.), you can oftentimes order replacement CDs for about $10 from them. Call them up and find out how much it will cost you and you may be suprised.

They will usually need:
Information needed to make the order (shipping address, etc)
Computer Model number (found on the back of the tower, on the side of the machine or inside of it on a sticker)
Computer Serial Number (found at the same location)
etc.

If you can't provide those (such as the case being swapped out and the original case being thrown out), it will of course be difficult (or likely impossible) to get new CDs.

---

### Post by kenwong on 2007-12-17
I'm having a problem similar to deafchickadee's.

Any idea how to make it work without resort to recovery CD from the computer manufacturer?

---

