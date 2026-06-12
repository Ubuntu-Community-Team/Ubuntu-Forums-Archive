---
title: "Clean Window 7 Install on dual boot system?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2010-01-20
A friend has a desktop dual booting Vista and Ubuntu 9.10.
He just got his free W7 install disc and wants to do a clean install of W7 and keep the Ubuntu partition untouched.

Heard there will be no problem installing W7 on the existing C-Drive where Vista is at present. Was told this would cause no problems and it will leave Ubuntu untouched.

The only problem I heard is that GRUB will be knocked out.
Is this true and if so what to you have to do to reinstall GRUB? Is it easy to put GRUB in again or is it easier to just clean reinstall Ubuntu 9.10 all over again?

---

### Post by wilee-nilee on 2010-01-20
Here is the grub2 wiki #11 is the key. I am assuming here that otherwise you know what your doing to safely install W7 with having any needed backups.
[https://help.ubuntu.com/community/Grub2#Upgrading](https://help.ubuntu.com/community/Grub2#Upgrading)

---

### Post by cybrsaylr on 2010-01-20
Thanks wilee-nilee.
Was told W7 disc can be clean installed like a Linux Live-CD by hitting F12 at start, then selecting boot off CD/DVD-ROM. He has nothing to backup on Vista since he seldom used it preferring to wait for W7. Anything he wants to save from using Ubuntu will go on another HDD. 

Was just wondering what will happen to GRUB?
That link has a lot of info to read.

---

### Post by Sylslay on 2010-01-20
You will need restore grub , using Ubuntu liveCD.
Is not very diffcult. At may last year I swap XP for Wn7 RC, and reinstall grub. 
2 command fom livecd terminal, 
don't remeber now

---

### Post by wilee-nilee on 2010-01-20
> **cybrsaylr said:**
> Thanks wilee-nilee.
Was told W7 disc can be clean installed like a Linux Live-CD by hitting F12 at start, then selecting boot off CD/DVD-ROM. He has nothing to backup on Vista since he seldom used it preferring to wait for W7. Anything he wants to save from using Ubuntu will go on another HDD. 

Was just wondering what will happen to GRUB?
That link has a lot of info to read.

I have never had to reinstall grub anywhere but I see links to other threads that that give instructions basically the same as the set in the #11 part of that link I think it is pretty straight forward. If you install W7 you will lose grub but the live CD of the Ubuntu install can easily be used to put it back in the MBR.

There are a couple of regulars on the forum who are very good at looking at the MBR situation if anything goes amiss. I would just be careful with the partitions, keeping them intact.

The only other thing I would check out is if your friends computer has a recovery partition that will now be dead space due to the W7 upgrade. So if you use the W7 disc to cold boot and install use the custom install you can delete and format the windows partitions if you want and actually do a clean install if needed in the area windows was in. My computer came with a recovery and a main XP, two partitions, so I had to do a fresh install and just deleted the 2 partitions in the custom install part of the W7 install. Vista can be upgraded so do what works.

---

### Post by kansasnoob on 2010-01-20
Boot into Ubuntu and from terminal run:

```
grub-install -v
```

That will tell you the version of grub, 0.97 is legacy grub and 1.97+ is grub2. Then you'll know which steps to follow to restore grub :)

Also, if it's truly a clean install of Windows, it's less likely to mess with Ubuntu if you delete the existing Windows partition before trying to install.

---

### Post by cybrsaylr on 2010-01-20
Thanks for all the help guys. It's a lot clearer now.
Believe his PC has a Vista recovery partition that I will delete then when putting W7 in to be able to use that space. 

His big worry was losing what he had on Ubuntu which him, his wife and kids now prefer using over Vista. They just didn't want to pass up on W7, since their new PC qualified for the free upgrade from Vista to W7.

---

### Post by cybrsaylr on 2010-04-17
OK guys need your help again.

Installed W7, it installed fine and knocked out GRUB.

Can't get into the Unbuntu partition that is still there.

Tried Live-CD and put this code in terminal 
> grub-install -v

but nothing happened. It won't execute.

What do I have to do to reinstall GRUB or run Ubuntu partition?

---

### Post by presence1960 on 2010-04-17
> **cybrsaylr said:**
> OK guys need your help again.

Installed W7, it installed fine and knocked out GRUB.

Can't get into the Unbuntu partition that is still there.

Tried Live-CD and put this code in terminal 


but nothing happened. It won't execute.

What do I have to do to reinstall GRUB or run Ubuntu partition?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

I will then give 2 commands to restore GRUB to MBR.

---

### Post by cybrsaylr on 2010-04-17
presence1960, 
After reading your post I decided it was easier to just reinstall Ubuntu. Took 9 minutes plus 20 minutes to update and I was good to go. All that was left was installing flash and now both W7 and Karmic are running fine as a dual boot system.

---

### Post by presence1960 on 2010-04-17
> **cybrsaylr said:**
> presence1960, 
After reading your post I decided it was easier to just reinstall Ubuntu. Took 9 minutes plus 20 minutes to update and I was good to go. All that was left was installing flash and now both W7 and Karmic are running fine as a dual boot system.

It would have taken less than a minute to download the script, execute it and paste the info back here. Then about a minute to restore GRUB from the Live CD from the two commands I would have given you.

But as long as you got it working is what matters.

Disregard the troll's reply above mine. people really make me laugh... :)

---

### Post by cybrsaylr on 2010-04-18
> **presence1960 said:**
> It would have taken less than a minute to download the script, execute it and paste the info back here. Then about a minute to restore GRUB from the Live CD from the two commands I would have given you.

But as long as you got it working is what matters.

Disregard the troll's reply above mine. people really make me laugh... :)

I never did anything like that before so it seemed a bit too complicated for me. Since Ubuntu installs so easy and fast I thought that was an easier option for me. Thanks anyways Ubuntu is running fine now on their PC.

Was going to post this but I see that MS fanboy managed to get the thread closed before I could respond.

---

### Post by lisati on 2010-04-18
Thread re-opened and cleaned up.

---

### Post by cybrsaylr on 2010-04-18
> **wwerawx2 said:**
> <snip>

Been using Ubuntu for about 4 years now and have had far less problems with Ubuntu than Windows. Have installed Ubuntu on several PCs with no troubles at all. 

My friends PC was running Vista and Ubuntu. They got their free upgrade to W7. It took a bit over an hour to clean install W7 but it knocked out GRUB which I knew would happen. I then clean installed Karmic which took 9 minutes, then 20 minutes to update and Karmic was fully operational, something not possible with Windows in that short a time. 

The reason I dumped Windows and Apple is because I was a tired of having them pick my pockets every couple years for a new OS and then having to pay for software and security protection. Linux has excellent free software that does everything M$ software does. 

I throughly enjoy being M$ and Mac free.

---

### Post by cybrsaylr on 2010-04-18
> **lisati said:**
> Thread re-opened and cleaned up.

Thanks for tidying up the thread!....O:)

---

### Post by lisati on 2010-04-18
> **cybrsaylr said:**
> Thanks for tidying up the thread!....O:)

That's ok. If there's anything that has been deleted/moved by mistake, feel free to let the forum staff know.

---

