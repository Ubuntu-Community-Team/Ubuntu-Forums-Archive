---
title: "Upgrading Ubuntu 10.04"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by new-2-linux on 2013-11-25
Hi
I have Ubuntu 10.4 and am wanting to upgrade to 13.10. 

I am updating programs at the moment and it comes up with a message: 
{Some of the packages could not be retrieved from the server(s). Do you want to continue, ignoring these packages.}. If I click ignore an error occurs where it {Failed to fetch (.deb line) Something wicked happened resolving (packages) no associated with host name.}.
What do I do for this? 

Then when I go to upgrade to Ubuntu 10.10 a message comes up { Not all updates can be installed. Run a partial upgrade to install as many updates as possible.} Then I select partial upgrade and the distribution upgrade windows comes up. Then an error windows comes up with the message
{ Error authenticating some packages: It was not possible to authenticate some packages. 
This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages:
libavcodec-extra-52
libavformat-extra-52
libavutil-extra-49
libdvdcss2
libpostproc-extra-51
libswscale-extra-0
w32codecs}
With the only option as close. 
This is all through Update manager.

How do I fix these problems to be able to update my computer.

Thanks Callum

P.S. I am not an advanced user so please dont used complicated computer lingo or abbreviations.

Thanks Again

---

### Post by Bucky Ball on 2013-11-25
10.04 is no longer supported which is why no updates. The only way to get to 13.10 via upgrading through Update Manager is 10.04 LTS>12.04 LTS>13.04>13.10, a long, tedious and problematic course of action.

The best option you have is a clean install of 13.10. My advice? Update 10.04>12.04 and wait until 14.04 LTS comes out next April. You can then update directly from 12.04 LTS>14.04 LTS and the LTS releases now have five years support. The interim releases (like 13.10) have nine months. 

I would do a clean install of 12.04 LTS personally (supported until April 2015) and take it from there. There were a lot of changes between 10.04 and 12.04, not least of which was the introduction of Unity as the default desktop environment rather than Gnome. 

PS: for 10.04>12.04 open Software Sources>Updates tab and 'Notify me of' ... set that to 'Long term support releases'. Going through all the releases from 10.04 LTS to 13.10 is just not feasible and will take and age and involve plenty of breakage. Don't go there.

PPS: You are not wanting to update the computer, you are wanting to upgrade the release. I have changed your thread title accordingly. ;)

---

### Post by new-2-linux on 2013-11-25
How do I go about a clean install of 12.04 as I am running Ubuntu 10.10 and Windows 7 as a dual boot?

---

### Post by Bucky Ball on 2013-11-25
10.10 not supported either (not since April 2012!). 

Download the ISO, make a bootable DVD, boot from it. When you get to the partitioning section of the install, choose 'Something Else' and install it directly over 10.10 (where 10.10 is currently located ... you will see it there, along with your Windows installed on an NTFS partition). 

ALWAYS make a backup of personal data before attempting a clean install (or an upgrade for that matter). 

Have a look here:

[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)

... and here:

[http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml](http://news.softpedia.com/news/Installing-Ubuntu-12-04-LTS-266201.shtml)

---

### Post by deadflowr on 2013-11-25
Simply put, as stated above, if you want to upgrade to 13.10, a fresh install is by far the easiest and less stressful way.

That aside, the packages that can't be authenticated seem to be of the medibuntu repository kind.
Medibuntu was shutdown, which is probably why those errors pop up.

But nevermind that
Download a clean copy of the version you want, burn it and make sure you back up what you want, and install fresh.

I'm a fan of the upgrader system Ubntu has, and it has worked great for me.
But one upgrade enough can be a pins and needles experience all on its own.
I can't imagine more than two in a row.
It would take quite a while and at any point could break, leaving you with garbage.

Edit: the above is for post #1.
It seems this thread jumped onto something different while I was typing.

You stated in post one you were on 10.04, but tried upgrading to 10.10?
Why didn't you upgrade to 12.04?
I didn't know the option to upgrade to 10.10 was still there.

---

### Post by Bucky Ball on 2013-11-25
> **deadflowr said:**
> 
But one upgrade enough can be a pins and needles experience all on its own.
I can't imagine more than two in a row.
It would take quite a while and at any point could break, leaving you with garbage.

+1. Exatamundo!

---

### Post by deadflowr on 2013-11-25
> **new-2-linux said:**
> How do I go about a clean install of 12.04 as I am running Ubuntu 10.10 and Windows 7 as a dual boot?

Good question.
The easiest way is when you start the reinstallation process you will get to a screen to select how and where it will be installed.
Several options will appear including install it side by side, use the whole disk, other ones I forget, and Something Else.

Of all these, choose something else.
Reason for choosing something else over the other options is because it will give you more control on what goes on.

In something else, a partition outlook screen will appear.
Somewhere listed is the ubuntu partition.
Notably, it will usually have an ext2,3, or 4 file system type.(Though several other fs types exist)
Ignore any other partitions especially any marked ntfs and any marked linux-swap.

Now, if the whole system is installed on a single partition and not divided with a separate home partition, highlight that partition and select change or edit.
In change or edit choose the file system type from the drop down.
And select the mount point (this is usually /, which is the whole thing)
Then select format.(The default for 12.04 and up is ext4, but I think 10.04 used ext2, so if used ext4 it will reformat anyway)
And the OK or whatever yes is in it (been a while since I ran it, but the generalities are the same)

If you did install with a separate home partition you will nedd to figure out which is home and which is root.
typically different sizes and the space used will help in that case.
but I think if you had a separate home, you would know all this already.

Now the part that can get most users in trouble, the bootloader.
When you get back to the partition outlooky window and it finishes re-setting itself up, before you click ok/install look at the bottom of the screen and there should be an option to select where the bootloader goes, pay attention to that and make sure it is set where it is suppose to go.

To find out where grub is
[http://askubuntu.com/questions/30341/how-to-know-the-partition-where-grub-is-installed](http://askubuntu.com/questions/30341/how-to-know-the-partition-where-grub-is-installed)

Once you set that all up, click install and finish following whatever the installer asks.

This should overwrite the existing system with a new one.
As such, I would recommend backing up all the files you want.
As they WILL be lost with almost guaranteed certainty.

There are ways the save a list of installed packages, but because the differences between what you are upgrading from, some packages might not even exist anymore, so it would probably be better in the long run to start from scratch and find out which are still there and which aren't.
my opinion alone though, other will think otherwise.

Hope the above is somewhat sane and makes some sense.
Good luck, in which ever way you go.

---

### Post by new-2-linux on 2013-11-25
I have the installer on a USB as I don't have a CD big enough. Do I install it from linux or from windows?

---

### Post by QIII on 2013-11-25
Your question makes me wonder if you are actually dual booting or if you have a Wubi install.

How did you install your current version?  Was Windows running when you installed Ubuntu?

---

### Post by new-2-linux on 2013-11-25
I purchased it for a tech guy in town who installed it all for me. I think i have a Wubi installed. 

I have the installer on a USB and have used Ubuntu to create a start up disk of it but it keeps getting stuck at 99%.

Am I able just to use the original download and install it from windows?

---

### Post by new-2-linux on 2013-11-25
OK. I have created a USB on windows using the way the Ubuntu website states to create the USB drive that will do the update. I have gone into both Ubuntu and Windows and the update has not come up in either. I then try to run the Wubi.exe file. On Ubuntu via wine it comes up with the options menu then when install is clicked it comes up with an error message. Then on windows the options window comes up but Only the windows partition is able to be selected. Do I get a disc and put the installer on it or do I just give up?

---

### Post by deadflowr on 2013-11-25
Ignore my previous posts as they have to do with a normal dual-boot re-installation matter.

Look over this and see what you may or may not be able to do with wubi
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I don't run wubi and haven't had the pleasure of upgrading a wubi install.
My understanding is that it is supported, somewhat, and possible.

In case you want to see about doing a normal dual-boot looky here
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Bucky Ball on 2013-11-25
There are not many Wubi gurus here as it is intended to try before an install to hard drive, not intended as a long term solution (Wubi has in fact been phased out and if you are using the 13.10 that is probably why you're having issues with it - the Wubi option is there but shouldn't be). As deadflowr says, disregard all previous advice. Most of it doesn't apply to Wubi and I also know nothing about it.

---

