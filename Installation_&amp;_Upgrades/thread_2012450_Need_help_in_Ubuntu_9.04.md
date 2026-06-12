---
title: "Need help in Ubuntu 9.04"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by edmund085 on 2012-06-29
I have recently installed Ubuntu 9.04 in this computer. I am new to Ubuntu since I am a Windows User. The reason why I changed to Ubuntu is because our instructor is using Ubuntu for Netowrk and Communiations. I chosed this specific Version of Ubuntu is because of my hardware specs. It is only Pentium IV, memory is 512 and the Video card is 256. Unless if you can reccomend me a version which is supported by my COmputer or latest, it will be fine by me. My problem is that I cannot install google chrome nor update the files in this OS. I always get an error "Error: Dependency is not satisfiable: libasound2 (>> 1.0.22)". So, I wanna ask if there is a solution for this, or what browser do I ned in order for me to use a flash player.

---

### Post by coffeecat on 2012-06-29
Ubuntu 9.04 is obsolete and has been unsupported for about 18 months now - no updates, no security patches. That is why you are getting the error message.

Please post full details of your graphics card - the chipset is the important piece of information - and people will be able to recommend a more up-to-date version of Ubuntu or another Linux distro that you could use. I don't see the Pentium 4 CPU being a particular problem, but 512 MB RAM is marginal for the standard gnome/Unity desktop that comes with Ubuntu; a lighter desktop such as comes with Lubuntu may be suitable. But an older graphics card is often a limiting factor and we need to know this.

---

### Post by black veils on 2012-06-29
you should try **Xubuntu 12.04** first, if it is too slow, try a tweak of **Swappiness**, if still too slow, then use **Lubuntu 12.04**, that should be good. i think 512ram can be worked with, given the right operating system etc.

if you have a problem with the appearance, the panels, window borders and wallpaper can be changed.

and use lighter alternatives for some of your applications, like email and office software.


[SIZE=3][COLOR=Green]_**get your operating system**_[/COLOR][/SIZE]

download [Xubuntu]("http://xubuntu.org/getxubuntu/")

download [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")


[SIZE=3][COLOR=Green]_**verify the integrity of your downloaded files**_[/COLOR][/SIZE]

the downloaded files md5sums are located [here]("https://help.ubuntu.com/community/UbuntuHashes/") , find the relevant names.

check your downloaded files [with this]("https://help.ubuntu.com/community/HowToMD5SUM")  (Scroll down to **MD5SUM with "Checksums calculator**)


[SIZE=3][COLOR=Green]_**create bootable installation media**_[/COLOR][/SIZE]

usb flash drive: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

cd/dvd: in [Windows]("http://infrarecorder.org/?page_id=5") , burn as image, and use slowest burning speed.

---

### Post by edmund085 on 2012-06-29
thanks for the advice. My friend also said that the Lubuntu is better for older systems, bUt is it same as the original Ubuntu? I was thinking of installing netbeans for Java programming and developing, and maybe this will decrease the performance. Is there other way to identify your Video card? Because all I can remember is its 256MB and since its my first time I have ben looking everywhere and no sign, it not like windows where you can have device managaer or system info or something. I wanna check my video card before migrating to Lubuntu in order to save work and time. :)

---

### Post by black veils on 2012-06-29
ubuntu 9.04 compared with ubuntu 12.04 is a big difference, then comparing ubuntu 9.04 with lubuntu is not that big a difference. it depends what you require. you will have to try and see. i suggest trying xubuntu first though because it has many useful features.

there are ways to check hardware info (which i cannot find right now), but you could look in your bios instead. try pressing F2 or F12 etc to find the right key for your computer which gets you into the bios.

---

### Post by edmund085 on 2012-06-29
I am using a PCI Video Card so theres no info on the BIOS. Is there other ways? I have been finding software and I have hard time installing them.

---

### Post by edmund085 on 2012-06-29
I would like to add also that I checked the xubuntu minimum system requirements. Works great but, is there software available for me to burn? Or how do I burn the LiveCD? Cause I really dont have any idea on how to do it on Ubuntu. :o

---

### Post by black veils on 2012-06-29
> **edmund085 said:**
> I am using a PCI Video Card so theres no info on the BIOS. Is there other ways? I have been finding software and I have hard time installing them.

i am not sure why you are needing to know this information, but it will be somewhere listed if you open Terminal, and enter this command ```
sudo lshw
```if you are searching the internet for drivers to install in ubuntu, that is not the correct method.

if you mean you are trying to install from the Software Centre (if they even had one back then), it wont work, because the version 9.04 is outdated.

---

### Post by black veils on 2012-06-29
> **edmund085 said:**
> I would like to add also that I checked the xubuntu minimum system requirements. Works great but, is there software available for me to burn? Or how do I burn the LiveCD? Cause I really dont have any idea on how to do it on Ubuntu. :o

the links i provided give all the info your need, the apps to use etc


Edit:

if you just need to know how to make a live cd within your ubuntu 9.04, you will have to use whatever burning software is provided, perhaps brasero. burn as image, and choose the slowest speed.

---

### Post by coffeecat on 2012-06-29
> **edmund085 said:**
> I am using a PCI Video Card so theres no info on the BIOS. Is there other ways? I have been finding software and I have hard time installing them.

@edmund085, open a terminal in Ubuntu 9.04 (if I remember correctly, you'll find it under Applications -> Accessories). Run this command:

```
lspci | grep VGA
```

That will give us details of your video card. Copy and paste the output into your post. If you highlight the terminal output with the mouse, you can right-click and copy.

The reason we need this information is that some older video chipsets are unsupported or badly supported with the more recent video drivers that come with more recent versions of Ubuntu. Let's see what you have to see if you are likely to run into this sort of problem.

How have you been finding software? For the same reasons that you cannot update 9.04, you cannot install software from the repositories, because the repositories are closed. (Unless you use the old-releases repository, but let's not go there.) If you are finding software on the internet to download, please stop there. Almost all the software you will need will be in the Ubuntu repositories and you do not have to hunt around on the internet the way you do with Windows. If you install a supported version of Ubuntu or one of its derivatives, you will be able to install what you need from the Software Centre.

---

### Post by edmund085 on 2012-06-29
ok, I have another update, I just upgraded my 9.04 to 10.10 or Meerkat. Well, I was happy to receive updates but theres a prompt saying that my version is no longer supported :(. Everything works fine as I have observed, no lagging or everything or maybe not yet, I thried the lspci | grep vga this is the result:

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)

I decided to change to Ubuntu 10.10 since I have a major headache finding old files in the repositories after researching and reading for hours. I have this 10.10 CD along with 9.04 burned 1 year ago because I used it to install an old PC. Now that I have restored it and fixed it to the working conditioned, I decided to used it but sadly those version become outdated. I wanna also know if that should I consider upgrading it to 11? since 10.10 is working fine after upgrading. I just wanna know any suggestion if it is recommended.

---

### Post by coffeecat on 2012-06-29
Let me clarify length of support for the Ubuntu releases. The release number is year + month. Hence 9.04 = 2009/April; 10.10 = 2010/October. All releases are supported for 18 months only, **except** the long-term support (LTS) releases which come out every 2 years. Current LTS versions are 10.04 which will be supported for another 10 months or so for the desktop version, and the latest release, 12.04, which will be supported for 5 years from last April.

You can see that the 11.** versions have limited remaining life - I'll let you do the maths.

Your Radeon 9200 card is old, but you *should* get reasonable performance using the default open source driver with the latest 12.04 release.

Here's a suggestion for you: download the ISOs for Lubuntu and Xubuntu 12.04 (if you have the bandwidth) and burn them to CD. Try running them live. If they run OK, then install. Better than trying to upgrade from an unsupported, non-updated installation. If you can spare the bandwidth, download the Ubuntu ISO as well and see how that performs with your hardware. I think it might struggle with 512MB, but it's still worth checking out. Be warned that running a live session from a CD is very slow. It's not a fair test of how it will perform once installed to your hard drive.

Xubuntu, Lubuntu and Ubuntu links for you. The download links are on those pages:

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by edmund085 on 2012-06-29
ok, I will try them both and I will post some details on what happen.

---

### Post by black veils on 2012-06-29
as we have answered, its time to move forward, you need to install either 10.04 (because its a long term support version), or 12.04 (the latest version which is also long term support). and it needs to be xubuntu or lubuntu due to ram.

10.04 lasts until April 2013

---

### Post by edmund085 on 2012-06-29
I have some good news and I also have bad news. The good news is that I will be receiving upgrade parts not later than December 2012. I also researched that 10.10 LTS will end on April 2013, since the next LTS will be on 12.04, right? So if that's the case I will wait for the new parts to arrive and then upgrade my computer to Linux 12, since it will be the best option I have. Anyways, the bad news is, My sound isnt working right I tried playing a video in youtube and there is no audio. I'm assuming that it has not been recognised or missing. How do you know if there's a conflict or an error or not recognised? ANd how will I know that the other devices are in error in something? I have been looking for an app like a Device Manager in the menu, and I don't have a clue what it is.

---

### Post by coffeecat on 2012-06-29
> **edmund085 said:**
> I also researched that 10.10 LTS will end on April 2013, since the next LTS will be on 12.04, right?

Was that a typo? 10.10 is not LTS and is past end-of-life. 10.04 is LTS and is supported until April 2013. We need to clarify which version you are running.

---

### Post by edmund085 on 2012-06-29
oh, geez....... My mind just got interchanged. I thought 10.10 is the LTS. I think I never read it thoroughly. I am using 10.10, I check the About Ubuntu on the System Menu and i saw the version 10.10 so I think its outdated. Is there any chances that in December I will still be receiving updates? Cause from what I have seen I have been able to make updates.

---

