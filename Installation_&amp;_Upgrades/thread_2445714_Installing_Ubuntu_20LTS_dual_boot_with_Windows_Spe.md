---
title: "Installing Ubuntu 20LTS dual boot with Windows: Speed, partition sizes"
date: 2020-06-18
forum: Installation &amp; Upgrades
---

### Post by Richard_York on 2020-06-18
Our current laptop, around 8 yrs old,  works fine on Ubuntu 18.04 for everyday use, but struggles with the new Covid need to use Zoom and a wish to edit some short videos. So I have an Asus laptop with manufacturer refurb on order, to arrive hopefully in a week or so.
Spec as in screenshot here:[ATTACH=CONFIG]286256[/ATTACH]

If I install Ubuntu, ( either 18  again or 20LTS), to dual boot on this new machine with Windows, will that limit its performance appreciably? 
I'm truly no computer geek, and and am rapidly out of my depth, but I don't like Windows, using it for updating the satnav & not much more. So I don't know if having both OS on one machine impedes its abilities.

Assuming it's going to be fine, I would welcome advice on how big to make the partitions for  Windows/Ubuntu when I do install on the new laptop, please, given how little we use Windows. 
I know it's a "how long is piece of string" question, but I guessed too small for Windows on this machine first time round, which may be why it crashed on updating, and had to be reloaded by the friendly local shop. So I don't want to guess wrong on and mess up the nearest thing to a new computer we've bought for around 20 years!

With many thanks.

---

### Post by CelticWarrior on 2020-06-18
Let's start with your new computer: Nothing to brag about. Surely newer than the one you already have but that may not mean what you expect, like newer= faster and/or newer=more powerful. Its i3 CPU is easily beaten by any 8 years old i7; 8GB of RAM is comfortable but surely not better than 16/32GB of 8 years ago, even if slower and from a previous "generation"; 1TB HDD is certainly much slower than any SSD of the aforementioned vintage; and lastly, the unmentioned graphics - likely some cheap integrated - is certainly no better than a dGPU Nvidia or AMD of that vintage. In a nutshell, maybe not as good as you hoped but time and usage will tell. 

Now, regarding the question > f I install Ubuntu, ( either 18  again or 20LTS), to dual boot on this  new machine with Windows, will that limit its performance appreciably?
The answer is NO, dual-boot has no impact on any one of the installed OSes' performance. However, when dual-booting anything with any Windows 8n or newer there are reasons to disable its Fast Startup feature. [Arguably, even if single-booting Windows, you should disable it anyway]("https://www.windowscentral.com/how-disable-windows-10-fast-startup"). So, that alone - Fast Startup off - will result in Windows booting just a tiny bit slower.

How much drive space to keep for Windows? This asks for opinions mostly. IMO, around 100-120GB for the main partition should be enough for installing some additional software and also comfortably update. Please pay attention and do NOT touch the ESP (EFI System Partition) - the Ubuntu installer should use that some partition and, preferably, do not touch vendor or Windows recovery partitions.

---

### Post by oldfred on 2020-06-18
Windows NTFS partitions really need 30% free, at 10% free there is not enough room to defrag. Linux needs some extra roomto run well, but not quite as much as Windows. 

I would remove HDD and just install a new SSD. That would improve performance a lot. If only using Windows occasionally you can just swap drives when needed. Windows UEFI install product key is now in UEFI, so you  can reinstall Windows, but may need any unique drivers from Asus.

---

### Post by Richard_York on 2020-06-19
Thanks both.
Celtic Warrior, I realise it's far from high-end, but hopefully compared to what I'm writing this on[ATTACH=CONFIG]286277[/ATTACH]  it's a useful improvement.
Thanks for the comments on partition space, that's helpful.

Funding is limited, so replacing the HDD with SSD may have to wait  a while, though I'm sure it would improve things more, OldFred.
When you refer to 10% and 30%, I need to ask what these percentages refer to, please.

Best wishes.

---

### Post by oldfred on 2020-06-19
The percentage is amount of free space the NTFS partition has.

---

### Post by Richard_York on 2020-06-25
I now have the Asus laptop, and need to re-partition. I'm working on the DIY principle of "measure three times, cut once" or in this case, "ask more before guessing!"  An ill-educated guess cost me a Windows re-load on the machine I'm using here, after all.

  Here's the current partitioning.
[ATTACH=CONFIG]286317[/ATTACH]
Every guide to re-sizing for Ubuntu which I read ends up with "choose your preference" or similar. I'm still too vague about what percentage of what is needed to have a firm figure as a preference, just the need for enough space to allow Windows to be stable with occasional use, but for Ubuntu, which we use for  98% of the time, to work at its best with plenty of headroom. 

So I'll be very grateful for a simple "shrink partition C to size (x)" type answer please. 

With thanks and best wishes.

---

### Post by oldfred on 2020-06-25
You are using 50GB in the NTFS partition. So 100 probably will work, but if you eventually want a major Windows update, it may need more space? And even if only using occasionally do you down load anything large like videos or lots of music?
Only use Windows to shrink NTFS & reboot immediately, so it can run chkdsk.

If you use Linux most of time, how much space do you typically need for it? And you do have another drive for backup of both Windows & Linux data?

I also do not like very large / (root) partitions. Ubuntu's default now is just / and if UEFI an ESP (or it will use the Windows ESP). I prefer / to be 25  or 30GB unless running server apps (Web, database, etc) that normally are in /.
If a newer user the separate /home easier as it sets ownership & permissions & mounts in fstab. You can create in advance with gparted and in Something Else choose to use it (change button) or create during install using Something Else install option.

But some like separate partition(s) for media, music or video or some other use. But too many partitions then can be a hassle to manage on where unallocated/available space is if another is getting full.
Only you can determine what you really want.

I find my optimal partitioning, after several years is not so good. But I only trust a hard drive or now SSD for a few years as main working drive, so start over with a new drive.

---

### Post by ActionParsnip on 2020-06-25
Remember. Ubuntu can access NTFS but Windows access to Ext4 is problematic. If you intend to share data between OSes then use NTFS (FAT32 if the files are smaller than 4Gb) to accommodate Windows' shortcomings

---

### Post by Richard_York on 2020-06-25
Thanks you.

I did once try to organise separate partitions, but quickly got out of my depth, so the simpler the better for me.

Unlikely to download large videos or much music, especially via Windows, we're more likely to have some large files of acoustic multi-track music recorded ourselves, and hopefully  video, ditto.
Because I'm retiring an old Vista 32bit machine from sound recording, and we've not tried videos before, it's hard to assess what typical future space used will be, hence my desire for simply as much as possible, within reason.

I'm wondering if maybe saving about 150 - 200 GB  for Windows would be adequate?

And yes to having another external drive to save data.

> 
"If a newer user the separate /home easier as it sets ownership &  permissions & mounts in fstab. You can create in advance with  gparted and in Something Else choose to use it (change button) or create  during install using Something Else install option.

As I'm still a basic user, this looks a useful paragraph to me to work on, though it'll need some unpacking. I install Ubuntu because we hugely prefer it to Windows, but will never be an advanced computer user.

I don't think I've needed to share data between OS's...  that's beyond my depth again :-)

Thanks for your patience!

---

### Post by Richard_York on 2020-06-26
Are the instructions for partitioning sufficiently good at     [https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/](https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/)     ? Quite a long scroll down before that section is reached, but the steps seem mostly follow-able after a couple of readings.

As usual, of course,  the sizes are left up to the user, which is why I've fought shy of this before, and simply plonked earlier Ubuntu editions into the space created by shrinking C partition.  Or maybe this would work adequately again here?  - fear of lousing it up through misunderstanding is always present!

There's still the matter of using GParted to fit in, as OldFred recommended in post #7

With thanks.

---

### Post by oldfred on 2020-06-26
Ubuntu's default install is just / (root). But on newer drives that are a lot larger than years ago when that design was set, it makes for a very large / in most cases.

Better to have separate /home and/or data partition(s). If sharing data with Windows, you will need a shared NTFS data partition, but you create that in advance or after Ubuntu install leaving space for the NTFS partition. If most of your data is in your data partitions, you do not need separate /home, but may want a slightly larger / (root) as some data may get stored there.  I have all data in separate data partitions and only use 7GB in new install & my older 18.04 grew to just over 12GB even with good housecleaning.

Ubuntu now creates a 2GB swap file, so do not create a swap partition. Although some with server type installs still suggest a slight larger 4GB swap partition.

```
fred@focal-z97:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda3      ext4   24G  7.2G   16G  32% /
/dev/sda1      vfat  499M   16M  484M   4% /boot/efi
/dev/sdb4      ext4  385G  110G  256G  31% /mnt/data

```

---

### Post by Richard_York on 2020-06-26
Thanks - understanding gradually improving here!  So "create [partition] after Ubuntu install" - does this mean that  as long as I've made space first by shrinking "C", I can leave out the GParted step, and achieve the extra partition(s)  during the installation? That would be one less risk. 

I've previously chickened out of that stage during installations, having shrunk "C" drive to make space, I've let Ubuntu find its own answer, trusting its decision more than my own.
If I get it wrong, I suppose a re-install second attempt is possible  ??  Irreversible steps are quite intimidating when taken in fog, albeit not complete dark now!

I'm also unaware how to assign partitions so that they are recognised as data partitions, rather than the place the OS installs itself.

---

### Post by oldfred on 2020-06-26
I do not like letting an installer automaticallly change partitions, so I only use Something Else.
With Something Else you have two options, one is just selecting a partition that you have previously created or want to reuse and telling installer it is / (root) and ext4. If separate /home you select /home & ext4. And if a reinstall you must NOT select the format box, or all your data in /home is erased. But you have good backups, so a mistake is never the end of the  world.

I use gparted to partition in advance & then Something Else to choose.

Second option is to create / & optional system partitions during install.
The installer is similar to gparted in creating partitions, if you have not created them in advance.

See howto's at bottom:
[https://gparted.org/documentation.php](https://gparted.org/documentation.php)

How to Install Ubuntu 18.04 Alongside With Windows - screenshots Something Else
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

---

### Post by Richard_York on 2020-06-27
That's truly helpful, much appreciated. Today's otherwise busy, will report back as soon as I get time to follow up. With so many "how to" pages, some of which are better than others, it's good to know which are reliable.

---

### Post by Richard_York on 2020-06-27
With apologies for yet more questions...

> **oldfred said:**
> 
Second option is to create / & optional system partitions during install.
The installer is similar to gparted in creating partitions, if you have not created them in advance.

Is it fair to say, given that I'm finding GParted info somewhat daunting, working with the Install "Something Else" section will be enough, even though you'd personally prefer GParted?

> 
See howto's at bottom:
[https://gparted.org/documentation.php   ]("https://gparted.org/documentation.php")

The UEFI Boot section would be good if I came to it with more understanding, I think. The quick scan I've had time for so far on the rest quickly goes out of my depth.

> 
How to Install Ubuntu 18.04 Alongside With Windows - screenshots Something Else
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)


That looks truly helpful. So if I basically slavishly follow steps from around the patch on Something Else, where the screenshot time moves to 09.12, that should work for me, I hope. Am I right that labelling a section as " EXT4 journaling file system" is enough for the computer to work it as data storage, or is there another step needed for this to work? 
I see at [https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)  the paragraph at the bottom, "Different file systems on the same disk" gives a dire warning, but I guess I'm not contravening that, am I?

Sadly this one: >  How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
 got me a "file not found" response.

There's [https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/](https://fossbytes.com/install-ubuntu-20-04-with-windows-10-dual-boot/)   if that's deemed OK.

One more for now, please - I downloaded Ubuntu 20LTS using this current laptop, and used the "Startup Disk" tool to make my bootable USB drive. Various "HowTo" sites advise Rufus as essential, but is there any reason why Startup Disk won't have done the job equally well? I've used it on earlier updates.

Thanks as always. I feel a whole lot nearer readiness for actually starting!

---

### Post by oldfred on 2020-06-27
Time to retire that old link.
I probably should check the links I post as many now are older, but differences between Windows 8 and 10 and all the Linux flavors are minimal, mostly graphics have changed somewhat.

---

### Post by Richard_York on 2020-06-28
Life is too short to check all links every time, especially when dealing with cartloads of questions from people like me :-)

Any comment on my other queries in #15. please?

---

### Post by oldfred on 2020-06-28
We find many users who have an issue with the installer.

Sometimes it is the flash drive, sometimes the downloaded ISO, sometimes just the port on the system used and sometimes the tool used to create the live installer. And in most cases we never know what issue really was. 

So whatever works is good.

---

### Post by Richard_York on 2020-06-29
One more, before I take the plunge.   

I still find the info on partitions & what each is used for, confusing, I'm sorry. So my concern is that if I set the partitions wrong it may impede what I can do with the machine.

* Please would you point at any serious flaws in my proposed route?  I'm sure there would be more optimal possibilities, but if this will work satisfactorily I think I can set it up.

Step 1: use Windows Disk Manager to shrink C partition from 930GB to 140GB, leaving me 790GB to play with.  Assuming I'm correct that "C" is where Windows continues to reside, I hope that should leave it plenty of headroom.
Step 2: use USB flash drive, hoping this works, to install.
Step 2:  During "Something Else" stage of install, assign 30GB for Ubuntu to reside in, which I think is / (root), and the remaining c.760GB as /home. Each of these to be chosen as EXT4 option.

* Ubuntu now creates its own Swap directory, you said, OldFred - should I assign something smaller than 760 as  /home to leave space for this?

Given my original received advice from a sound/video engineer, that to work with video or sound recording, I'd need 8GB RAM and 500 GB available hard disk, I'm hoping this will do the job.

... or have I completely misunderstood? It's sadly possible!

With thanks and good wishes.

---

### Post by oldfred on 2020-06-29
That will work.

I like to have multiple installs and separate partitions for some things. Back with XP 10 years ago I also had a Shared NTFS data partition so I could use XP & Ubuntu with some of the same data. 
But If later you want more partition(s), you can just shrink /home. Too many partitions starts to lead to size management issues, so always a trade off.

Do you have good backups, always most important step.

And be sure to boot install media in same boot mode as Windows. UEFI or BIOS.

---

### Post by Richard_York on 2020-06-30
That's encouraging!

But sadly a new problem:  when I tried to shrink the Asus C partition from 930GB to 140GB, it insists I can only shrink it to [ATTACH=CONFIG]286344[/ATTACH]47 and some, leaving me far less to play with than planned. This is, I realise, a Windows problem not Ubuntu, but it's currently a block on further progress.

It's a newly manufacturer refurbished machine, which I have only used to set up with such as it needs to start up in Windows 10, but but no further use so far.  One screenshot image, no other data stored.

 The laptop I'm using to write this only comes with 365GB on disk, but allowed me, using Disk Manager in Windows, to shrink its C partition far smaller than that before installing Ubuntu 18.04.lap

I don't know if  downloading Easeus   [https://www.easeus.com/partition-manager-software/windows-cant-shrink-volume-partition.html](https://www.easeus.com/partition-manager-software/windows-cant-shrink-volume-partition.html) or
Aomei   [https://www.diskpart.com/articles/shrink-c-drive-3889.html](https://www.diskpart.com/articles/shrink-c-drive-3889.html)   would be a safe  & sensible solution.... and also within my capabilities, without getting into deeper water.

* Alternatively, a more radical route - this laptop dualboots into Windows and will hopefully go on doing so, for the rare occasions we need it.
 I could simply do a clean install and get rid of Windows on the Asus. Am I right to believe that laptop processors are marked in such a way that if I did need to have Windows re-installed, the licence would still be there and a re-load would be all that was needed, rather than paying for new software?
It's very tempting.

Yours gratefully.

---

### Post by oldfred on 2020-06-30
You need to change some settings in Windows to allow the shrink.

How to Get Around Windows&#8217; &#8220;Shrink Volume&#8221; Inadequacy Problems
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
Hiberfile in Windows 7, 8 & 10 often prevents shrink
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by Richard_York on 2020-07-01
Thanks as always for all your patient and helpful replies!

---

### Post by Richard_York on 2020-07-02
OldFred, with some shame I reveal that when the links in #22 opened with the warning that this was serious Geek level stuff,  I chickened out! We have Windows on this old laptop, so I decided to go for what seemed the less stress option of a clean install of Ubuntu 20. This forum is not the place for personal stories, but I have the remains of Chronic Fatigue, and am prone to meet a wall when things get too deep.
Sadly I'm now in deeper water. Because it's a different cause - install freezing - I will start a new thread if I can't find the solution in existing threads. I can't actually mark this one as Solved, but I'm sure your solution would have worked had I had enough know-how.

---

### Post by oldfred on 2020-07-02
I thought it was just turn off hibernation & the hiberfile & run a defrag. I used to run defrag weekly on my old XP system but have not used XP for 10 years.

---

### Post by Richard_York on 2020-07-02
Ah well, as I said, between meeting my energy wall and the "advanced Geeks" warning, I faltered at the last jump! I had also set myself a deadline to get the thing working, always a bad idea, and that deadline is now past, so I'll take it a little more leisurely this time.
Thanks again for your answers - at least I now have a better understanding of partitions as a result, which will be useful, so it was not wasted.

---

