---
title: "Xubuntu Installation incredibly slow.. then stops!"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by mike_9000 on 2007-02-27
I am trying to install Xubuntu on a 750Mhz PC with 128Mb of Ram. The 20Gb Hard drive has been formatted using Fdisk from a Windows ME boot disk. 

I have checked the integrity of the installation CD I am using with the built-in tool, & it's fine.

My problem is that the installation process moves more slowly than a glacier, always getting stuck on step 2 of 6 (where you select your time zone). I try to select London but , whatever I do, the system always decides that I *really* want New York, then refuses to proceed.

I already run Ubuntu on a more powerful machine & love it. Please, someone save me from having to use Windows ME on my older machines!

---

### Post by K.Mandla on 2007-02-27
I think I would try installing to a blank (unformatted) drive, and let Xubuntu partition the drive as it wants.

If that doesn't do anything, see if it helps to install a command-line version, then install *xubuntu-desktop*. If you need ideas, there's a page in the wiki that talks about the old ways of installing Xubuntu ... [uwiki]InstallingXubuntu[/uwiki]

---

### Post by skywatcher on 2007-02-27
For what it's worth, I have tried several times to install Dapper on my desktop PC, without success, but on my laptop, no problem. Then I noticed that it sometimes stopped at the first step (language choice), sometimes at the second step (place and time). That made me think that it must be memory. So, I checked the system in Windows, and it showed that I had 248MB. I then installed an additional 256MB, and tried the installation again. This time it worked like a dream...

---

### Post by mike_9000 on 2007-02-28
Success! 

It *was* a memory problem. 

Apparently, Xubuntu will run happily on 128Mb of RAM or less - but needs over 190Mb to handle the graphical installation that comes with the standard disk. 

The solution seems to be to download the Alternate CD, which does not have the 'live' feature & handles the installation process from the keyboard with a series of DOS-like dialog boxes. 

This uses a lot less memory & gets in under the wire. It's running now, & going as smootly as my previous Ubuntu installation.

Thanks for the support, people!

---

