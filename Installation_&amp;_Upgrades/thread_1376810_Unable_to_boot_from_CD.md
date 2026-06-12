---
title: "Unable to boot from CD"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Vusys on 2010-01-09
Hi all,

I have a Dell Inspiron 1525 and I've been trying to boot into the live mode. I can get into the main 'Try Ubuntu without any changes' menu, but selecting that option causes the CD tray to spin up, followed by the head audibly flailing about for a minute or two causing the laptop to noticeably vibrate, followed by nothing. It doesn't boot or give any errors, it just stops. I can read the discs just fine in Windows.

So far I've tested shipit CDs of 9.10, 9.04 and 8.10. All cause the above problem. 8.04 works perfectly.

---

### Post by phillw on 2010-01-09
> **Vusys said:**
> Hi all,

I have a Dell Inspiron 1525 and I've been trying to boot into the live mode. I can get into the main 'Try Ubuntu without any changes' menu, but selecting that option causes the CD tray to spin up, followed by the head audibly flailing about for a minute or two causing the laptop to noticeably vibrate, followed by nothing. It doesn't boot or give any errors, it just stops. I can read the discs just fine in Windows.

So far I've tested shipit CDs of 9.10, 9.04 and 8.10. All cause the above problem. 8.04 works perfectly.

Hi & welcome to the forums.

A couple of things to check.

[LIST=1]
[*]Check the image you downloaded --> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[*]Burn the disk at 4X speed, if your driver cannot do this then --> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  has a section on CD burning
[*]Check the md5 of the burned cd, as per step 1
[/LIST]
If you have a cd/dvd drive cleaning disk, it's always helpful to give that  a blast.

If you're using the CD's shipped to you from Canonical, then You really need to be cleaning your CD drive.

There is always the option of USB if your computer supports usb booting (and, to an extent, even if it doesn't)

Regards,

Phill.

---

### Post by Vusys on 2010-01-09
> **phillw said:**
> Hi & welcome to the forums.

A couple of things to check.

[LIST=1]
[*]Check the image you downloaded --> [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[*]Burn the disk at 4X speed, if your driver cannot do this then --> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  has a section on CD burning
[*]Check the md5 of the burned cd, as per step 1
[/LIST]
If you have a cd/dvd drive cleaning disk, it's always helpful to give that  a blast.

If you're using the CD's shipped to you from Canonical, then You really need to be cleaning your CD drive.

There is always the option of USB if your computer supports usb booting (and, to an extent, even if it doesn't)

Regards,

Phill.

I don't think it's a problem with the drive or discs. I can read the discs just fine in Windows, and I can boot successfully from other discs on the same laptop.

As for installing via another method, you're right, it would work. But it's not ideal. It's more than a little worrying if something as basic as the installer has problems.

---

### Post by phillw on 2010-01-09
> **Vusys said:**
> I don't think it's a problem with the drive or discs. I can read the discs just fine in Windows, and I can boot successfully from other discs on the same laptop.

As for installing via another method, you're right, it would work. But it's not ideal. It's more than a little worrying if something as basic as the installer has problems.

Well, you cannot have it both ways.. either ..

[LIST=1]
[*]the Installation CD is poorly
[*]The CD drive is poorly (bear in mind that iso files, such as a ubuntu install disk, run to far tighter tolerances than file browsing & listening to music / watching dvd's etc)
[*]The computer is poorly - Or you're trying to put the wrong architecture of operating system on to the computer (such as 64 bit onto a 32 bit one)
[/LIST]
Running the md5checksum on the CD will narrow it down to drive or CD, if it fails - if it passes, then I suspect you've got the wrong architecture of CD for your machine.

The installer works - the problem lies else where - All we've got to do is find out where.

Regards,

Phill.

---

### Post by Vusys on 2010-01-10
> **phillw said:**
> Well, you cannot have it both ways.. either ..

[LIST=1]
[*]the Installation CD is poorly
[*]The CD drive is poorly (bear in mind that iso files, such as a ubuntu install disk, run to far tighter tolerances than file browsing & listening to music / watching dvd's etc)
[*]The computer is poorly - Or you're trying to put the wrong architecture of operating system on to the computer (such as 64 bit onto a 32 bit one)
[/LIST]
Running the md5checksum on the CD will narrow it down to drive or CD, if it fails - if it passes, then I suspect you've got the wrong architecture of CD for your machine.

The installer works - the problem lies else where - All we've got to do is find out where.

Regards,

Phill.


[LIST=1]
[*]One CD maybe, but three? And they're all ones produced by Canonical. Either way, I put the 9.10 one in a different PC and checked it for integrity. It came back fine.
[*]Again, maybe. But I seriously doubt it. I have a whole stack of bootable CDs here. All of them work, except for Ubuntu 8.10 and above. Which implies to me that 8.10 and above have some kind of problem with my laptop that previous versions didn't.
[*]It's a 32 bit computer with a run of the mill Intel Core 2 Duo processor. The disc is a 32 bit one.
[/LIST]

---

### Post by derekmbarnes on 2010-01-10
Question: are you shutting down your system first and starting it fresh to boot the CD, or are you just restarting the computer? (For reasons beyond my understanding, this makes a difference.)

---

### Post by Vusys on 2010-01-10
> **derekmbarnes said:**
> Question: are you shutting down your system first and starting it fresh to boot the CD, or are you just restarting the computer? (For reasons beyond my understanding, this makes a difference.)

Just tried both. No difference for me.

---

