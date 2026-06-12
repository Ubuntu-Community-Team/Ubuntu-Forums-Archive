---
title: "Ubuntu 10.04 Lucid Lynx on an MSi Wind U100"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Puzzled Guy on 2010-06-25
Hi!

I have an MSI Wind U100 with windows xp and ubuntu 9.04 on it. I'm planning to install 10.04 on it soon.

Any "gotchas" I should look out for? Is the screen flicker fixed yet?

---

### Post by dino99 on 2010-06-25
only take care to install grub2 on the ubuntu partition (remove grub1 and menu.lst if you use it)

[http://www.google.com/search?as_q=u100%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=u100%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=lang_en&cr=&as_ft=i&as_filetype=&as_qdr=m&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by Puzzled Guy on 2010-06-25
I have 3 Ubuntu partitions: one mounts as '/', one as '/home', and one as swap.

I'm running 9.04 and I'm planning to do a *clean install *of Ubuntu 10.04. Specifically, I'm going to format the / and /home partitions using the manual partitioning option (want to test out that new ext4 file system) anyway so I don't think I'll have to worry about menu.lst at all.

Although, I don't know what you mean by "take care to install GRUB2 on the Ubuntu partition". Could you be a little bit more specific? After all, the installer for 10.04 and 9.04 differ in some ways and I only have experience with 9.04

Do you mean that somewhere in the installer, there will be some sort of pop-up asking me where to install GRUB2? If there is something like that, what should I tell it? (A screenshot or two would be nice, I can't seem to find one)

Thanks

EDIT: OK. I've finally finished downloading the Ubuntu .iso file. I checked the md5sum and it was correct. But I want to gather some more information first. I might be able to install it next week. Until then, feel free to post here!

---

### Post by Puzzled Guy on 2010-06-26
Oh man! My brother just dropped our external hardrive! Good thing it's not broken. My dad was smart enough to buy a shock-proof drive, and given how clumsy my brother is, it was an intelligent choice.

Why am I talking about an EHD? Because I'm gonna back up my data on that thing so that I can use my 8 Gig USB stick as a LiveUSB.

---

### Post by wordstar on 2010-06-27
Hi Puzzled guy. Some models of MSI wind had a compatibility problem with their network card running on Ubuntu.  I am using a MSI U100x running on Ubuntu 8.04, I had issues when the 8.04 was upgraded to newer kernel versions so I have to load an older kernel version to be able to connect to the internet, I couldnt connect to the internet as there was no network card detected by later versions of 8.04...  I have been afraid of upgrading ever since.  Are you currently using a later version of ubuntu on your wind?  If so, how is the networking performance doing?

---

### Post by Puzzled Guy on 2010-06-27
Well currently, I'm using 9.04 Jaunty Jackalope. I had a bit of trouble with the internet at first but I got it fixed. Wireless works great, too.

How do I find out the exact model of my msi wind u100?

---

### Post by goldfox_79 on 2010-06-27
> **Puzzled Guy said:**
> Hi!

I have an MSI Wind U100 with windows xp and ubuntu 9.04 on it. I'm planning to install 10.04 on it soon.

Any "gotchas" I should look out for? Is the screen flicker fixed yet?

The screen flicker is fixed (Ubuntu 10.04 + MSI U123).

---

### Post by Puzzled Guy on 2010-06-28
I hope that fixing the flicker doesn't involve updating the BIOS. That means more work to do. I'll just test out the LiveCD and see if it flickers or not.

---

### Post by Puzzled Guy on 2010-06-29
Ok...
Attempting LiveUSB boot now...
Let you know if it works.

UPDATE:
WOO-HOO! It works! And pretty darn good too!

I'm posting this from an Ubuntu 10.04 LiveUSB session.

OK, here's what I can tell:
1. The screen flicker seems to fixed (in the live session at least, anyway).
2. The wireless works (I am able to connect wirelessly to my Prolink H6300G Router).
3. I'm able to connect to the Internet without problem (otherwise, how could I be telling you guys this?).
4. Theme's now a darker, less eye popping purple and black (was getting sick of that shi* colored theme anyway, too bright).
5. The only color on the top panel is the icons.
6. In my old installation, visual effects didn't work (don't know why) but in the live session, they do work.

Ubuntu 10.04 seems fit for installation. And I'm ready for it too. I've got my data backed up on an external hard drive.

I'm planning to do manual partitioning and format my /home and / partitions so I can have the ext4 file system (and also because my settings were getting a bit cluttered and I want to start fresh).

OK!

See you Friday. I'll be installing Ubuntu then

Never mind. IMMAH DOIN' IT NOW!

---

### Post by Puzzled Guy on 2010-06-29
Hooray!

I just successfully installed Ubuntu 10.04 Lucid Lynx. I formatted my / and /home partitions to ext4. The wireless card works out of the box.

I not experiencing any kind of screen flicker, distortion, warping, or whatever. The black and dark purple them looks good, easier on the eyes.

Now it's time to start updating, adding new repositories, install ubuntu-restricted-extras, install OpenShot (a great video editor), and last but not least: Email my dad about the success of the installation.

I think I can mark this thread as solved. ):P Bye! Thanks for all your help!

---

### Post by wordstar on 2010-07-10
> **Puzzled Guy said:**
> Well currently, I'm using 9.04 Jaunty Jackalope. I had a bit of trouble with the internet at first but I got it fixed. Wireless works great, too.

How do I find out the exact model of my msi wind u100?

There's a big sticker under the computer.  Mine says U100x

---

