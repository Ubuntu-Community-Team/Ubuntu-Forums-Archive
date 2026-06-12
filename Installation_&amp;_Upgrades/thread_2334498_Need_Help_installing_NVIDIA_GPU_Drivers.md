---
title: "Need Help installing NVIDIA GPU Drivers"
date: 2016-08-20
forum: Installation &amp; Upgrades
---

### Post by RJLiberator on 2016-08-20
Hi all,

Fresh install of Ubuntu (latest version I suspect) on a brand new desktop computer.

I have installed a NVIDIA GTX 1060 graphics card and I want to install it's drivers. I figured I would go to the website ([http://www.geforce.com/drivers](http://www.geforce.com/drivers)) and manually download the driver, but this didn't seem to work for me as when it finished loading, I got an error. (I'm trying this method again).

There seems to be a lot of different ways via a Google search, and I've been trying, but no luck yet going through terminal.

Can anyone walk me through getting my Nvidia driver set up? 

Thank you.

---

### Post by Bucky Ball on 2016-08-20
Update your install and then check in 'Additional Drivers'. There should be an NVidia driver there for you waiting to go. No need to install from a third-party or via the terminal. Simply enable the driver in 'Additional Drivers'.

For newer hardware, best to use newest release: 16.04 LTS. Is that a very new card? Hopefully the latest driver in Additional Drivers will deal with it. Others may be able to confirm. Good luck.

* PS: Just having a sniff about and it definitely works with Ubuntu somehow, going on [the experiences of others]("https://duckduckgo.com/?q=NVIDIA+GTX+1060+ubuntu&t=hi&ia=web"). Try the above first and let us know how it goes.

---

### Post by RJLiberator on 2016-08-20
Hi Bucky Ball,

Thanks for replying so quickly.

I believe my install is up to date. I checked Additional drivers and still nothing. 

Is there any way I can make sure my install is up to date? This is a brand new desktop build.

---

### Post by Bucky Ball on 2016-08-20
Open Software and Updates> Other Software tab. Do you have the Canonical Partners repository enabled? If not, enable, update and have another look in Additional Drivers. You may also need to install ubuntu-restricted-extras which is also in the repositories (Software Centre or whatever it is now called).

---

### Post by RJLiberator on 2016-08-20
When I try to update it tells me "Failed to download repository information". Hm. 

I did enable the Canonical partners repository just now.

---

### Post by Bucky Ball on 2016-08-20
Ah. That may have something to do with it but indirectly. Perhaps post a new thread regarding that error and you might end up fixing the GPU driver problem in the process. The driver should be appearing in Additional Drivers and as it's not it could point to this repo issue. 

When you post that new thread, include the contents of this file:

/etc/apt/sources.list

Also post a link to the new thread here if you like and I'll take a look.

(Reason I suggest a new thread is that your new issue has nothing to do with the title of this thread - and perhaps nothing to do with the GPU issue at all - and a new thread will improve your chances of support specific to your repo issue. I will suggest this: change the mirror in Software and Updates and see if that makes any difference. If yes, let us know how Additional Drivers looks. If not, start that new thread and include the fact you tried a different mirror as well as posting the file mentioned previously.

You haven't by any chance recently done a release upgrade and still have some of the repos hanging about from the previous release or another third-party, manually added PPA?)

---

### Post by Bashing-om on 2016-08-20
RJLiberator; Hello;

Before returning to the update situation, addressing a graphics driver:
[http://www.nvidia.com/download/driverResults.aspx/105343/en-us](http://www.nvidia.com/download/driverResults.aspx/105343/en-us)
nVidia recommends the 367 version driver for your stated card.
That driver is available from our trusted PPA and is not available in the software repository.
That is not to say a lower version driver will not work that is available in the repo .
It is up to you what you want to try .

For the update situation.
what results presently with terminal commands:
```

ping -c3 8.8.8.8
ping -c3 ubuntu.com

```
to begin isolating where the fault may lie.

[INDENT][INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RJLiberator on 2016-08-20
Thank you, mate.

[https://ubuntuforums.org/showthread.php?t=2334501&p=13533454#post13533454](https://ubuntuforums.org/showthread.php?t=2334501&p=13533454#post13533454)

```
ronald@Ron-Jon:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=49 time=18.2 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=49 time=20.3 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=49 time=17.5 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 17.507/18.680/20.323/1.201 ms
ronald@Ron-Jon:~$ ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=50 time=101 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=50 time=102 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=50 time=103 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 101.544/102.373/103.134/0.650 ms
```

---

### Post by Bashing-om on 2016-08-20
RJLiberator; So far so good.

We know there is not a networking issue, and I see no problem with your sources.list file.

So, show what results:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]forward the progress
[INDENT][INDENT][INDENT]in fault isolation
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RJLiberator on 2016-08-20
```
ronald@Ron-Jon:~$ sudo apt update
Hit:1 http://mirror.steadfast.net/ubuntu xenial InRelease
Hit:2 http://mirror.steadfast.net/ubuntu xenial-updates InRelease              
Hit:3 http://mirror.steadfast.net/ubuntu xenial-backports InRelease            
Hit:4 http://mirror.steadfast.net/ubuntu xenial-security InRelease             
Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
ronald@Ron-Jon:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ronald@Ron-Jon:~$ 

```

---

### Post by Bashing-om on 2016-08-20
RJLiberator; Hey !

That says there is no problem.
What now :
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```

as we ponder what to do for a graphics driver.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by RJLiberator on 2016-08-20
```
ronald@Ron-Jon:~$ sudo ubuntu-drivers devices
== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

ronald@Ron-Jon:~$ sudo ubuntu-drivers list
intel-microcode
ronald@Ron-Jon:~$ 

```

---

### Post by Bashing-om on 2016-08-20
RJLiberator; Yuk !

Totally unexpected result . System not seeing the graphics card ! .. Is it enabled in bios ?

As a double check.
what returns:
```

sudo lshw -C display
lspci -k | grep -EA2 'VGA|3D'

```

If bios does not pass to the kernel what is
[INDENT][INDENT][INDENT]the kernel just does not know
[/INDENT][/INDENT][/INDENT]

---

### Post by RJLiberator on 2016-08-20
Ah, interesting result!

```
ronald@Ron-Jon:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
ronald@Ron-Jon:~$ lspci -k | grep -EA2 'VGA|3D'
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1c03 (rev a1)
    Subsystem: Gigabyte Technology Co., Ltd Device 3716
    Kernel modules: nvidiafb, nouveau


```

So perhaps I need to enable the GPU in BIOS?

---

### Post by Bashing-om on 2016-08-20
RJLiberator; Well ..

I do see it that the graphic's card is not identified . Hardware troubleshooting, however, is not my strong suite .
Sure could be, not enabled in bios ??
Might be of benefit to see what X thinks .
Post back:
```

cat /var/log/Xorg.0.log

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by RJLiberator on 2016-08-20
I just did a fresh install as I was having an enxryption problem everytime I started my computer up. 

This fresh install, however, is worse than before. My screen is extremely tiny now. 

I'm trying to update and follow the steps as previously.

If it is a hardware issue, perhaps I messed up on a connection to the GPU in my first built PC. 

I will check in with things later (tonight or tomorrow).

Thank you for your help tonight.

---

### Post by Bashing-om on 2016-08-20
RJLiberator; Ho Kay  - not .

I am done for the night . 
I will check back in tomorrow ,

[INDENT]regards
[/INDENT]

---

### Post by Bucky Ball on 2016-08-20
This:

```
ronald@Ron-Jon:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
ronald@Ron-Jon:~$ lspci -k | grep -EA2 'VGA|3D'
```

... shows you have no driver installed for the card which is probably why it is unclaimed. Back to the original problem and point of the thread. Perhaps because it is so new the open-source driver has no idea what it is so can't help. Also why you have a small screen. 

You might want to try the repository Bashing-om mentioned some posts ago before it headed down the update problem road.

Can you now run these commands without error in a terminal?

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by RJLiberator on 2016-08-20
here's what I get:

```
ronald@iwin4ron:~$ sudo apt update
[sudo] password for ronald: 
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:3 http://archive.canonical.com/ubuntu xenial InRelease
Get:4 http://security.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [373 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [368 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [319 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [316 kB]
Fetched 1,566 kB in 0s (2,096 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
ronald@iwin4ron:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by RJLiberator on 2016-08-20
Damn, I have no idea what to do or what's causing this. 

My screen resolution is extremely small and it essentially cuts off the bottom of the screen.

I keep fresh installing Ubuntu and trying slightly different things (I have some UEFI or generic device to boot, tried both, didn't work).

---

### Post by Bucky Ball on 2016-08-20
Don't think reinstalling is going to make any difference so wouldn't bother. If you have Ubuntu installed and it's working, small screen or not, then it's all good. Have you tried installing the PPA Bashing-om suggested, as suggested? What does 'sudo lshw -C video' show now, please?

I'm figuring this is now about the missing GPU driver so matter of figuring out how to get the one that doesn't sound like it's made it yet to Additional Drivers. You have checked in there again in the new install? Once you have the correct driver installed you should be able to change resolution. For the moment, have you looked in the Display settings and tried to change resolution there?

Just to confirm; you are using Ubuntu 16.04 and you downloaded the ISO [from here]("http://www.ubuntu.com/download")?

---

### Post by RJLiberator on 2016-08-20
> 

I take it you are using Ubuntu 16.04 and you downloaded the ISO from here?

Yes.

>  Have you tried installing the PPA Bashing-om suggested, as suggested???

I'm not sure. I don't think I have done this. How do I go about doing this? 

> What does 'sudo lshw -C video' show now, please?

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff
```

---

### Post by Bucky Ball on 2016-08-20
And I have edited mine. Sorry. I try and avoid that ...

---

### Post by RJLiberator on 2016-08-20
> For the moment, have you looked in the Display settings and tried to change resolution there?

I have tried this, but the reso is so small i can't even get to the point to change it. 

> you have checked in there again in the new install? 

Yes, I check in the additional drivers section quite a lot in the hope that it miraculously ends up being there. :)

---

### Post by Bucky Ball on 2016-08-20
Ok, go back to the link you posted in your first thread. ;) NVidia suggest the 367.35 driver for your card and also the very new and beta 360, neither of which are in Additional Drivers in 16.04. Other web pages have confirmed the 367 works with your card so download that one to your downloads folder, [see post #1 here]("https://ubuntuforums.org/showthread.php?t=239797&p=1399268&viewfull=1#post1399268") to install the .run file you just downloaded, then reboot.

You will need to change the filename in the how-to to the name of the file you download: NVIDIA-Linux-x36_64-367.35.run, but basically, navigate to your downloads folder in a terminal and

```
sudo chmod +x NVIDIA-Linux-x36_64-367.35.run
./NVIDIA-Linux-x36_64-367.35.run
```

... should work. You might need sudo in front of that second command too. Not sure. Good luck and let us know.

---

### Post by RJLiberator on 2016-08-20
Ah, this seems like a smart move.

When doing so I get ERROR: nvidia-installer must be run as root

---

### Post by RJLiberator on 2016-08-20
Okay, now I put "sudo" in front of the ./Nvidia....run 

And now the error is

ERROR: You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Bucky Ball on 2016-08-20
Edited my post. Please check, but you need to put 'sudo' in front of whatever command you're getting the error from.

---

### Post by RJLiberator on 2016-08-20
Okay so I did something strange by following the errors:

Based on this thread: [https://ubuntuforums.org/showthread.php?t=1916961](https://ubuntuforums.org/showthread.php?t=1916961)

and post #6

I was able to install something. My resolution is now fixed. I'm not trying to understand what it just did. If I installed the correct driver, etc.

---

### Post by RJLiberator on 2016-08-20
I must go to work now, I will be back in this thread later tonight to make sure everything is working properly! Thank you again for your great help.

---

### Post by Bucky Ball on 2016-08-20
Great news. Post this when you can. The output of 'sudo lshw -C video'. This will clearly show what driver your GPU is using.

---

### Post by RJLiberator on 2016-08-21
The output is as follows:

```
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:45 memory:fa000000-faffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:fb000000-fb07ffff


```


Although, when I go to NVIDIA X server settings it tells me that I am using driver 367 which is the one I should be using. 

Everything *seems  *to be working really well. I now have great reso as 1900 x 1200 with both of my monitors on dual monitor setup.

---

### Post by Bucky Ball on 2016-08-21
Bingo.

driver=nvidia

... is what you have installed (this entry was missing previously if you check your other postings of the output of that command) and if NVIDIA X config is telling you 367.35, double bingo. We have a winner!

Congrats and well done. Please mark thread as solved to help others and enjoy (use Thread Tools at top right or see second link in my signature - this will not close the thread to further discussion, just helps future travelers. :))

PS: Eventually the 367 should appear in Additional Drivers. As the card is very new it probably just hasn't made it there yet. Consider yourself an 'early adopter' as you've had to go the longer route with it. Doubt this will be necessary in future. I have the GTX 970, fairly new when I got it, but the correct drivers were right there in 16.04's Additional Drivers for it. Yours is perhaps just a bit too new. Nothing wrong with that. ;)

---

### Post by Bashing-om on 2016-08-21
:)

well done !

---

### Post by RJLiberator on 2016-08-21
Thank you both for the wonderful help. I greatly appreciate it.

---

### Post by Bucky Ball on 2016-08-21
All good and thanks for marking as solved. Your thread will help others with this card until the driver lands in Additional Drivers which, as mentioned, it probably, eventually will. :)

---

