---
title: "upgrade 7.04 to 10.04"
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by nevscott on 2010-06-16
Installed 7.04 on a toshiba satellite M115 Laptop. I want to upgrade to 10.04. Made a boot disk and tried to launch but 7.04 always opens. How can i get this upgrade done?

---

### Post by nevscott on 2010-06-16
help with ubunto upgrade from 7.04 to 10.04.

---

### Post by oldos2er on 2010-06-16
I think it would be best to do a fresh install of 10.04. To upgrade from 7.04 to 10.04, you'd need to step through each version of Ubuntu from 7.10 on, which isn't possible because 7.10 (and 8.10) has reached its end-of-life. Not to mention that'd be an awful lot of downloading.

---

### Post by nevscott on 2010-06-16
I made a live cd of 10.04 and changed the bios to boot from cd but version 7.04 keeps opening.

---

### Post by oldos2er on 2010-06-16
Did you burn the ISO file as an image?

---

### Post by nevscott on 2010-06-16
I'm not sure what that means. I just had the files written to the cd. What does it meas burn as an image?

---

### Post by mi_di on 2010-06-16
> **nevscott said:**
> I'm not sure what that means. I just had the files written to the cd. What does it meas burn as an image?

No, you have to specify you are burning an image. Brasero gives this specific option for you.

---

### Post by irv on 2010-06-16
I use a program call K3B.
Just follow my screen shots.
[ATTACH]160659[/ATTACH][ATTACH]160660[/ATTACH]

---

### Post by jkid on 2010-06-16
check if u save changes after you put the cd rom to  boot firts

---

### Post by zellbz on 2010-06-16
I have a similar problem but im already on 10.04 but i am trying to reinstall. i using a usb and burned the iso using start up disk creator but when i restart my netbook to boot from usb it just start up my original 10.04 again. What's the problem? I keep asking this question with no response from the community!

---

### Post by irv on 2010-06-16
> **zellbz said:**
> I have a similar problem but im already on 10.04 but i am trying to reinstall. i using a usb and burned the iso using start up disk creator but when i restart my netbook to boot from usb it just start up my original 10.04 again. What's the problem? I keep asking this question with no response from the community!

Does your BIOS have a setting to boot from a USB and is it set to boot first? Also if it is set you can just hit the F8 or F12 key to get a boot menu on some PC's.

---

### Post by zellbz on 2010-06-16
> **irv said:**
> Does your BIOS have a setting to boot from a USB and is it set to boot first? Also if it is set you can just hit the F8 or F12 key to get a boot menu on some PC's.

Yes, it says [Removable Dev.] and i dont think i said my usb was called that before i install linux

---

### Post by irv on 2010-06-16
> **zellbz said:**
> Yes, it says [Removable Dev.] and i dont think i said my usb was called that before i install linux
Linux does not change anything in the BIOS, that is a EPROM chip on your motherboard. It stands for Erasable/programmable read only memory and is written to when you change setting in the BIOS itself. Your computer read this chip at boot time. The other memory is RAM, random Access Memory.
Removable Dev is your USB or any other thing you can remove like a memory card if you have one in your computer.

---

### Post by oldos2er on 2010-06-16
> **nevscott said:**
> I'm not sure what that means. I just had the files written to the cd. What does it meas burn as an image?

Here's a howto: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by zellbz on 2010-06-16
> **irv said:**
> Linux does not change anything in the BIOS, that is a EPROM chip on your motherboard. It stands for Erasable/programmable read only memory and is written to when you change setting in the BIOS itself. Your computer read this chip at boot time. The other memory is RAM, random Access Memory.
Removable Dev is your USB or any other thing you can remove like a memory card if you have one in your computer.

So any idea how i can go about reinstalling 10.04?

---

### Post by snowpine on 2010-06-16
Have you tested your bootable USB device on another computer to see if it works?

---

### Post by zellbz on 2010-06-16
> **snowpine said:**
> Have you tested your bootable USB device on another computer to see if it works?

it works on other computers and on my Xbox.

---

### Post by irv on 2010-06-16
you can do a google search and find things like:
[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

The point being you have to make sure you USB stick is boot-able before you can boot from it. Many of the question you are asking are on the Internet or on this board, you need to make a little effort to find them. The Link I gave you above was very easy to find.

If you can't get your PC to boot from a USB or CD you might have to see if you can find someone local who know about PC's to help you.

---

### Post by afrazin on 2010-11-23
> **oldos2er said:**
> I think it would be best to do a fresh install of 10.04. To upgrade from 7.04 to 10.04, you'd need to step through each version of Ubuntu from 7.10 on, which isn't possible because 7.10 (and 8.10) has reached its end-of-life. Not to mention that'd be an awful lot of downloading.

I found a site that has all the versions of Ubuntu ([http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)).  I want to upgrade from 7.04 to 10.04-LTS.  It's on our server and i really don't want to go through the hassle, time and money of starting off clean on a new server that we don't need.  Do you think if i go through the various versions that it might be able to upgrade without complications?  What order should I go in?  7.10 first or 8.04-LTS or what?

Thanks!

---

### Post by oldos2er on 2010-11-23
> **afrazin said:**
>  Do you think if i go through the various versions that it might be able to upgrade without complications?  

In my opinion, no. that's an awful lot of system changes, consequently a bigger chance of a screw-up somewhere along the process. Besides, every Ubuntu version from 9.04 below has reached its end-of-life.

If I were you I'd look into installing 10.04 server (if your business allows); it's an LTS release supported until April 2015.

---

### Post by afrazin on 2010-11-23
just an update for reference.  i found the page [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) which describes how you can go from 4.10 all the way through to 10.04.  as i was going from 7.04 i missed probably some of the harriest parts of it, but the 7.04 to 7.10 was fun.  in any event, it successfully brought me up to speed all the way to 10.04-LTS, just to let you all know.

---

### Post by irv on 2010-11-24
Before you do anything, read this thread.
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")
I tried this and it worked great. But before you start, make sure you make a list of installed apps. You will want to do this so you can reinstall them. Believe me it is much faster and less headaches then going through all the upgrades. The key is using the same user name and password and do not format the drive. You will see this in the post I link too.

---

### Post by oldos2er on 2010-11-24
> **afrazin said:**
> just an update for reference.  i found the page [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) which describes how you can go from 4.10 all the way through to 10.04.  as i was going from 7.04 i missed probably some of the harriest parts of it, but the 7.04 to 7.10 was fun.  in any event, it successfully brought me up to speed all the way to 10.04-LTS, just to let you all know.

You are brave! Good luck to you.

---

### Post by anechoic on 2010-11-25
the link in Irv's post stated:
'5. Pick old / partition, set it to be this install's /, and UNCHECK THE "FORMAT" CHECKBOX. This is key.'
I had reformatted the '/' partition and was wondering why 'UNCHECKING' the format checkbox was key? anyone know?

---

### Post by gregb49 on 2010-11-26
> **irv said:**
> Before you do anything, read this thread.
[http://ubuntuforums.org/showpost.php?p=9933073&postcount=11]("http://ubuntuforums.org/showpost.php?p=9933073&postcount=11")...The key is using the same user name and password and do not format the drive. You will see this in the post I link too.Thanks. I'm now using 10.4. My gOS 8.04 was beginning to be problematic. This suggestion worked fine and very quickly, with only minor niggles that I'm just sorting out now.

---

### Post by irv on 2010-11-27
I also plan on using this the next release. I saved the link so I don't forget how to do it. When you hit 72 like me, you have a problem forgetting thinks. Sometimes I wished the computer in my head worked a little better.

---

