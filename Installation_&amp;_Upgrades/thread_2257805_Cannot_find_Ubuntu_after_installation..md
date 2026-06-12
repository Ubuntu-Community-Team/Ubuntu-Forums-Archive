---
title: "Cannot find Ubuntu after installation."
date: 2014-12-22
forum: Installation &amp; Upgrades
---

### Post by alexbb2 on 2014-12-22
OK, this is what happens. Yesterday I downloaded [Ubuntu desktop 64 bit]("http://www.ubuntu.com/download/desktop") and decided to install it. In my Dell R5400 machine I have Windows 7 on C: disk and Windows Server 2008 on B: disk. The B: disk is a part (partitioned off) of the second internal hard disk, it takes about 300 GB. It is a huge dsik, 1.5T. So, I made sure that the rest of it, about 1100 GB were properly formatted, etc. I burned a CD image for Ubuntu .iso file, changed the boot sequence and began installation. Everything seemed to go well but when I restarted the computer, **there was no Ubuntu in the Boot sequence, **only Windows 7 and WinServer.

Another thing that struck me was that that installer did not want to place Ubuntu on this huge disk (1100 GB), instead, it partitioned it into three parts: 1) 548.47 GB, the other one of similar size and the third one - 16 GB. When I looked at the first partition, I found there only one file: **bootsqm.dat**.

I've been posting in a Linux forum and they mentioned two things: **Grub** and **Gru**. I have no idea what they are. Also I followed some guidelines from this [website]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html") but so far have not been able to make any progress. So far I have tried to install the Ubuntu four times. Starting with the second time I got a message*: Your computer already has Ubuntu installed. Do you want to erase it and replace it with a new installation?*

Now, I am not entirely new to Ubuntu. For a year or so I have worked with Ubuntu Virtual Machine under Oracle Virtual Box but in the end, I ran out of memory. I have made some mistakes while setting it up and now I cannot change anything. Mostly I do GFortran stuff. Thanks, hope for help.

P.S. Of course, I would refer to to have Ubuntu installed on my hard disk and have dual boot as I mostly use Windows 7 and Ubuntu. But I can also settle for a variant when I have Ubuntu boot loader on a flash memory stick or whatnot and have all files on the hard disk. I don't know if it is an options.

---

### Post by nerdtron on 2014-12-22
> Starting with the second time I got a message[I]: Your computer already has Ubuntu installed. Do you want to erase it and replace it with a new installation?
[/I]
You probably installed Ubuntu successfully. But I think on a server especially with multiple drives and multiple partitions you should not use the default auto install. And definitely don't use the option "Erase ubuntu and replace with a new installation" since this will also erase the other OS on the hard drive Ubuntu is installed on.

Testing out Ubuntu installation on Virtual machine is always a good idea.

If you really want to install Ubuntu now, since you already setup your partitions, you should choose the option "Something Else" to take you to the manual partitioning and installation screen. This is where you can point Ubuntu on where to install it self so as not to harm any other partition currently on you server.

The link you have provided is quite good. Now when you are on the Manual partitioning screen, before you click the Proceed/Install button, post your screenshot here and let's see what you done so far and we'll advise if it is correct and will achieve what you want.

---

### Post by alexbb2 on 2014-12-22
Thank you for answer. I tried "Something Else" but it did not work for me. When I was presented with the choice of selecting the hard disk and I chose the one which I designated for Ubuntu (548 GB) I got an error:

> No root file system is defined.
Please correct this from the partitioning menu.

Thus I had to back off and do the re-install option.

Sorry, I cannot keep posting anymore today, until perhaps about 5 hours from now: family gathering, etc. I am on vacation. Thanks for answering though. I appreciate it.

---

### Post by nerdtron on 2014-12-22
Yup, that error seems correct as you also need to define you mount points. 

Like I said, screen shot on this part of the installation would help us see your situation and provide better input.

---

### Post by alexbb2 on 2014-12-22
Well, how am I going to do the screen shot if it is all almost a DOS situation. With a camera perhaps? I may try tomorrow. Also how can I define the mount points?

---

### Post by grahammechanical on 2014-12-22
This is how to do it. We choose the Something Else option and the partitioner presents us with a list of partitions. Make sure that the correct hard drive is on display and then select the partion you want Ubuntu installed in. You need two. One for Ubuntu and one for swap but there may already be a swap partition from the previous attempts to install.

Select the partition and click Change. In the little dialog go to the panel labelled Use As and from the drop down menu select Ext4. You may see another dialog pop up. Tick to format the partition and go to the panel labelled Mount Point and select / from the drop down menu. Click OK.

If there is already a swap partition, then the installer will automatically use it. You may find it is the 16  GB partition. By default the Grub bootloader will install onto sda. That is the first Sata hard disk. If you want to leave the Windows boot loader on sda and you are installing to a second hard disk we can tell the installer to put Grub in sdb. There is a panel with a drop down menu to do that.

Regards.

---

### Post by nerdtron on 2014-12-23
> **alexbb2 said:**
> Well, how am I going to do the screen shot if it is all almost a DOS situation. With a camera perhaps? I may try tomorrow. 

When you boot the to the Ubuntu live CD, choose "Try Ubuntu". This will take you to the desktop Ubuntu which you can do screenshots and open the web browser.
Now click the "Install Ubuntu" from the desktop and then choose the "Something Else" option. That is where you enter the manual partitioning screen and set the mount points. You need a screenshot here.

> Also how can I define the mount points? 
The link you are following, on the bottom part. It is defining mount points like swap, /home, /, partitions.
We can guide you through the installation as long a you provide screenshot so that we can view your current partitions.

---

### Post by alexbb2 on 2014-12-23
Thank you guys, many times. I will try my best today.

---

### Post by alexbb2 on 2014-12-24
OK, I am back here. So far, after some additional attempts to install Ubuntu, I am back to the square one: no installation. Since you pointed it out to me I always choose "Something Else" but the stumbling block appears at the next step. I get an error message that no root file system is defined and offers me to correct this by using partition table.

You asked for the screenshots. I took them with my camera and it seems everything is visible there. Last time I tried to follow grahammechanical's instructions beginning with "This is how we do it." The problem is the **Change** button is dimmed. Plus and minus signs next to it are also dimmed. I don't remember if they were dimmed during my previous attempts to install the Ubuntu. After I click the quit button I get Ubuntu desktop with all the beautiful tabs and buttons and the file system but it is sort of illusory. I am a stubborn person and I must find a solution one way or another, but it is getting a bit frustrating. I guess I need more help here.

Thanks for working with me. Merry Christmas. - Alex.

---

### Post by westie457 on 2014-12-24
Looking at screen shot 4, the one with the list of partitions and the error window.
Obviously close the error then click the partition you want to use and click Change. Then follow the excellent advice already posted by grahammechanical.

You won't be able to use the one marked /dev/sda, use the free space marked with 1500301 MB to create the necessary partitions for Ubuntu.

---

### Post by alexbb2 on 2014-12-24
Thank you. Will try it tomorrow.

---

### Post by alexbb2 on 2014-12-25
Merry Christmas! I just tried to install Ubuntu again following the instructions by grahammechanical to the letter. I actually printed the whole threat out. The installation went exactly as it is supposed to, however, when I restarted the machine **there was no Ubuntu** in the start up menu. Do you call it Grub? If not what is Grub anyway?

Also I do not see any disk with Ubuntu installed like I can see Windows 7 (Disk C:\) for instance. It is invisible. Why?

So, where shall I go from here? I need my Ubuntu. I have dozens of GFortran programs waiting for me. Please, help. Why do thinks get so difficult for me? Thanks, - A.

---

### Post by oldos2er on 2014-12-25
It would help immensely if you could run the [bootinfo script]("http://bootinfoscript.sourceforge.net/") and post the RESULTS.txt file here, or post it on pastebin and give us a link. It will allow us to see exactly what's going on.

Does your computer use any of the following; GPT disks, UEFI, or Secure Boot?

---

### Post by westie457 on 2014-12-25
Hello again. Grub is short for Grand Universal Boot-loader or something very similar. When installed properly manages the start up of any OS installed on your computer.

To aid us to help you could you boot your computer using the media you created into 'Try' mode.
Then assuming your wifi is not working connect an ethernet cable open Firefox and go to [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
On this page scroll down to 'Option 2' and follow the instructions to download and install.
BootRepair should run auto magically. Do not attempt any repair just yet. All we require at the moment is that you post the link to the report that will be created.

After perusal of this report we should have a clue what has gone wrong.

Thank you.

---

### Post by alexbb2 on 2014-12-25
Thank you guys. I want to let you know that I just read the last two posts but most likely I will have to postpone any action until tomorrow morning. Family gatherings, etc. have taken emotional toll. Sorry. I appreciate your help immensely.

Still it is kind of strange that Ubuntu cannot install. BTW, with all manipulations Ubuntu wiped out my second Operating system: Windows Server 2008 although I am not grieving. But I know if I take an installation disk for the server and re-install it again I will be able to use it again in a moment. So, why is Ubuntu behaving differently. How come I cannot install it?

---

### Post by nerdtron on 2014-12-25
See my post previously #2
> And definitely don't use the option "Erase ubuntu and replace with a new  installation" since this will also erase the other OS on the hard drive  Ubuntu is installed on.

You probably is not installing the boot loader correctly while you are doing the manual partitioning part.
Like I said, you should probably let us see the screenshot of you manual partitioning before you click the proceed/install option on Ubuntu. 

Another thing on the bootloader is that you should set the first boot priority on the BIOS to be the hard drive on where you want to install Ubuntu.

---

### Post by nerdtron on 2014-12-25
If you are really having a hard time understanding all these manual partitioning and mount points, the easiest way to install Ubuntu is to disconnect all other hard drives.

Just leave one hard drive connected and then install Ubuntu. Once successful, you can then add the other windows drives.

---

### Post by alexbb2 on 2014-12-26
Of course, I don't understand mount points or rather I do have somewhat rudimentary understanding. In the mean time I also wiped out all the files from one my external hard drive yesterday and noticed it only this morning. All my family photos were there for some 15 or 20 years. If anybody has any experience with recovery software I will appreciate suggestions.

But the real bottom line is that it is Ubuntu's fault that all such problems are created. Had I tried to install a Microsoft OS of any sort nothing like this would have ever happened. The ridiculous side is that I am now hooked up on Ubuntu after years of working with Windows, Sql Server, etc. So I need to plow ahead.

I will be back but perhaps not today. Thanks.

---

### Post by alexbb2 on 2014-12-28
OK guys. I have something to tell you. Although I appreciate your willingness to help at every step, I am also a little bit angry with you and I will explain why. If you look at the cascade of posts for the past weeks you will see pretty much the same problem I've experienced. People install Ubuntu and cannot get the first boot. What does it tell you? It told me eventually, after so many attempts and wasted days that the newest version** Ubuntu Desktop amd64.14.04.1** is **bugged**. It has given me a lot of trouble, wiped out my precious software and wasted a week of my vacation. The point I am making is that you should have known about it yourself.

Fortunately, yesterday I found an **.iso** file: **Ubuntu-12.04.3-Desktop-i386.iso** in my Download folder. It crossed my mind to try to install it. I've used the Ubuntu from this file for more than a year in my Virtual Machine but as I mentioned in my OP, although I followed all official Oracle VirtualBox recommendations, I allocated too littley memory for it and I could not even run my GFortran programs eventually and also no update could be performed.

So, this morning I began installing **Ubuntu 12.04.3** and here I am. I am posting this from Ubuntu!!!! There is a double boot, everything. The installation went like a knife through butter!!! I chose the first option, not *Something Else* because the first option promised me a double boot, and it delivered. Now the Ubuntu is running the uipgrade to** 14.04**.

Well, still my problems are not over. My C:\ drive is a WD Velociraptor which is 10,000 rpm. This disk I installed Ubuntu on is 1,500 GB 7200 rpm. I do have another, new disk Lenovo 600 GB 15,000 and I would have liked to get the Ubuntu on this disk but for some reason I was afraid to use it after so many problems. Also, the Ubuntu I installed now is 32 bit and I actually need 64 bit. Somehow I need it all accomplished. I may still have some troubles ahead.

If you have any **reliable** suggestions how I can switch to 64 bit Ubuntu I will listen. Thanks, - Alex

---

### Post by alexbb2 on 2014-12-28
OK, some additional information. The system upgraded the OS and now I presume it is **14.04**. I also notied two problems at least. When I was installing Ubuntu **12.04.3** version, I got a usual message: "remove the installation media from the tray (if any) and click Return." I removed the media (CD), clicked Return and the Ubuntu froze. I have to crush the machine with the start button. The same thing happened after the upgrade to **14.04**. I had to crush the machine after I got the message that the upgrade was completed and I had to restart the machine. It actually offered me a "Restart" button which I clicked. The system froze. As I said, I had to crush the machine again. 

Now I was able to boot to Ubuntu however. After the desktop showed up I got a dozen or so messages that there were errors in some software and the OS itself and asked me to report the problems. I did. Now I will see if I can boot to Windows 7. I did it already once before the upgrade. Will see how everything works. A.

---

### Post by alexbb2 on 2014-12-28
OK, now I got dual boot: Windows 7 and Ubuntu 14.04 and everything seems to be working but there are some problems. One of them: I cannot shut Ubuntu off. Neither Shut off or Restart work. Ubuntu simply hangs up there and I have to use the Start button to shut the computer down. Besides once in a while a white window appears saying that a problem was detected and asks me if I want to report it. I usually say Yes.

---

