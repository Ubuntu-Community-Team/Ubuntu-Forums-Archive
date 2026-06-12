---
title: "1st time using Ubuntu. Ran 7.04 Live CD. Now can not boot Windows XP :("
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by enthusaroo on 2007-04-17
HELP!

That's all I have to say at this point. 

First off, I ran Ubuntu "Fiesty" 7.04 Beta off a Live CD today in order to test Ubuntu before I make the full install. I LOVE Ubuntu. Once this mess is sorted out, I DO want to make it my main operating system for this computer.

I have a Lenovo/IBM Thinkpad R60e that I bought just a few weeks ago. One of the Intel video driver files under Windows XP Home became corrupt. I went through hell trying to reinstall the video drivers with no luck. Even the Thinkpad technical support place in Hong Kong was unable to fix it. But this is a whole 'nother story. Finally, I decided "enough is enough" and decided to download Ubuntu today. I know the final release of 7.04 comes out on the 19th, so I decided just to make a live CD of the beta tonight to test it.

Actually, my plan was to use IBM's Recovery and Rescue program to "restore Windows to it's factory state". I wanted to restore Windows XP Home to it's original "just left the factory" state and then find a way to duel book my computer to have both Ubuntu and Windows XP. 

I did not get that far. In fact, I have not gotten anywhere.

I booted the Ubuntu 7.04 Beta live CD. Everything with Ubuntu works like a dream! I love it. Linux is everything I expected and more. 

THE PROBLEM is when I try to restart my system, I should expect it to automatically try to boot into Windows XP as usual, right? WRONG.......

IF I have the Ubuntu live CD in the CD/DVD ROM drive then it will boot Ubuntu. However, if I DON'T have the live CD in the CD/DVD ROM drive then it simply will boot into IBM's Rescue and Recovery program. There seems to be no way to get it to boot into Windows XP or find an option to boot into Windows XP. 

ACTUALLY, the main problem is I simply want to restore my system and Windows XP back to it's "original factory condition" with all of the original files. However, when I try to do this in the Rescue and Recovery program I get the following error message: "Product Recovery failed to restore your system". I figure it has something to do with the fact that I can't even boot up Windows! This problem began three hours ago after I first booted the Ubuntu live CD. Therefore, I'm assuming that perhaps Ubuntu changed something related to the "boot loader". After searching Google for an hour, I came up with some results. It turns out there should be a file located here: /file system/boot/grub/menu.1st.... However, in this beta of 7.04.... this file seems to not exist.

I'm at a lost. I don't know what to do. This is my first time using Linux/Ubuntu. I simply want to find a way to restore my system back to it's original factory state using Rescue and Recovery and also be able to boot-up Windows XP.

Two other problems related to fixing this issue that I should note.
1) I bought this Thinkpad brand new. However, as it turns out, when I bought this computer it did not come with any Windows XP disk. Therefore, I have no sort of back-up of Windows or way of reinstalling. My only hope is the IBM Rescue and Recovery program, which is suppose to be able to reinstall Windows by itself; but in my case I got the following error:
"Product Recovery failed to restore your system"
2) I am currently on work assignment in China (I'm originally from the U.S), so it's impossible for me to get to an IBM service center to have them assist with me with these errors. My only hope is that I may be able to get some advice on here to try to resolve the issues all by myself.

---

### Post by Blackforge on 2007-04-17
Some of those Recovery disks use an existing folder on your existing Windows partition to "reset" everything.  Others have a dedicated FAT32 partition.  In either case it doesn't all the necessary files on the CD, it just looks in those folders/partitions for the files to do a "factory reset".  You will need a real recovery CD with all the files if this is the case.  Sorry, but a good majority (if not all) computer companies are doing this.  If you wiped the partition to install Ubuntu you wiped the recovery folder/partition.

Since you're in China, you can always go knock on Lenovo's door. :D 


Appears I was right.  See here:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R60e](http://www.thinkwiki.org/wiki/Installing_Ubuntu_on_a_ThinkPad_R60e)

---

### Post by Neobuntu on 2007-04-17
Again, you can not lose Windows by just running a live CD, as the post title infers. Something else has to be done/changed.

This appears to be a duplicate post to the longer one.

---

