---
title: "Intrepid tester WARNING: Corruption of Intel e1000e Gigabit Cards"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jdong on 2008-09-23
**Everyone:** [i]This thread is left open for commenting and for users to provide relevant advice/updates. However, I ask for everyone to **exercise consideration and good judgement** when posting. 

Also, please fully read this post before running around in circles and submitting articles to Digg.[/i]

**STAFF:** *This post was written based on the best information I could find from the linked resources and kernel mailing lists at the time I wrote it. If additional information or factual inaccuracies are discovered as time goes on, feel free to edit this to your liking*

Latest updates log at the bottom.
------------------



[http://linux.slashdot.org/linux/08/09/23/133258.shtml](http://linux.slashdot.org/linux/08/09/23/133258.shtml)

By now a lot of you probably saw the above Slashdot article warning of "bricking" the Intel integrated e1000e network card by using Linux kernels version 2.6.26 and newer (most seen in 2.6.27 series). The cause of this bug is under investigation by RedHat, Novell/SUSE, Ubuntu, the Linux kernel developers, Intel employees, and other involved parties, a fix will not be available until it can be reliably reproduced.

So, the warning is: **There may be a possibility that booting the 2.6.27 kernel found in Intrepid and other recent distributions causes your Intel integrated e1000e network card to be unuseable until it is "fixed" by some not well understood process**. It is wise to refrain from testing such recent distros if you are not willing to accept this risk.


** Myths About Scope **

As seen on the bug report: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555)

There seems to be a lot of mass hysteria since this bug has been reported by the popular news sites out there. The bug has been reported on a relatively minor scale (I can count less than 5 reported cases in total on all the mailing lists referenced), so it probably is a "bad luck" scenario rather than a sure guarantee of a broken network card.

Also, there's no evidence that the "Bricking" is permanent yet -- it may or may not be reversible; just at the moment it's not well understood exactly what is wrong with the card given the difficulty of reproducing the bug and the lack of debugging information.

*UPDATE*: A post to Slashdot reads:
> 
I work on the e1000 team (including the e1000e driver) and here is what we know. A panic in another driver (believed to be the gfx driver but uncertain) which scribbles over the NIC/LOM non-volatile memory (NVM). This is only happening with the 2.6.27-rc kernels on ICHx systems. Since the NIC/LOM VNM is part of the whole BIOS image other things in the system could be effected by this driver panic as well. An update of the system BIOS will restore the NIC/LOM to be operational. We have some patches under test right now that we will be releasing later today to protect the NIC/LOM NVM. That should help narrow down who is scribbling over NVM.

The explanation sounds plausible but I have not personally verified the source ([http://linux.slashdot.org/comments.pl?sid=972935&cid=25119553](http://linux.slashdot.org/comments.pl?sid=972935&cid=25119553)). If it is correct, that means this problem is the result of another random event (some crashing driver) and isn't necessarily limited to the e1000e cards.

** What you should do **

If you are daring enough to want to help with this bug and have an e1000e card you like to bravely sacrifice to testing this bug, see the comment: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555/comments/22](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555/comments/22) . This contains a command you can run to "back up" the NVRAM in case this bug happens which will make it easier to reverse. If you don't "back up" this data and become afflicted by the bug, again, it's not clear how easily reversible it will be.

** What you shouldn't do:**
If this bug bites you, you shouldn't panic and try unapproved fixes. Don't follow random instructions on some wiki or list or download some random utility someone claims works. There is already confirmed information from Intel employees that some of these proposed utilities (IABUTIL.EXE) will **permanently brick** the card.

Wait for advice from a trusted kernel developer or Intel resource.


You also probably shouldn't break out pitchforks asking for the pulldown of all Ubuntu development releases or claim this affects 80% of the Linux using population.


** Testers Beware **

As this scenario teaches us, **DON'T ASSUME** a limited scope of possibilities implied by the cliche'd warning:
```

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

```

Or any of the other testing warnings about prerelease software. Yes, we are in the day and age where hardware is malleable enough for software to damage it beyond repair. No, the scope of risk from testing beta software isn't limited to just loss of data or the need for an OS reinstall.

------
**UPDATES:**

Update 1: Slashdot post added to scope section
Update 2: Thanks to plun (comment #2) for pointing out Intrepid just uploaded a blacklist of the e1000e module. I got confirmation on IRC that this indeed prevents those resources from being mapped into memory and subjected to this random corruption. It also means your e1000e network card will not be usable in Intrepid unless you load this driver explicitly. Also, this change is not in the Intrepid Alpha 6 and below LiveCD's.
Update 3: The e1000e driver is **DISABLED** on the upcoming Intrepid Beta. Following the beta, all daily CD spins and subsequent releases incorporate a fix for this bug and reenables the driver (safely). There is still no update on how to reverse this problem once you've been bitten, though it seems like that is in the works.

---

### Post by plun on 2008-09-23
> module-init-tools (3.3-pre11-4ubuntu10) intrepid; urgency=low

  * **Temporarily blacklist e1000e.**
    The e1000e driver is currently believed to cause onboard flash checksum errors in
    the 2.6.26 through 2.6.27-rc7 series kernels. These checksum errors
    can become severe enough to permanently disable the operation of the
    ICH8/ICH9 based e1000e NICs.

    For reference, please see:

    [http://bugzilla.kernel.org/show_bug.cgi?id=11382](http://bugzilla.kernel.org/show_bug.cgi?id=11382)
    [http://news.opensuse.org/2008/09/22/serious-e1000e-driver-issue-in-sle-11-beta-1-and-opensuse-111-beta-1](http://news.opensuse.org/2008/09/22/serious-e1000e-driver-issue-in-sle-11-beta-1-and-opensuse-111-beta-1)
    [https://bugs.launchpad.net/suse/+source/linux/+bug/263555](https://bugs.launchpad.net/suse/+source/linux/+bug/263555)

    This is hopefully a temporary measure.
    LP: #263555



[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007455.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007455.html)


.

---

### Post by plun on 2008-09-24
> **linux (2.6.27-4.6)** intrepid; urgency=low

  [ Tim Gardner ]

  * [B]Disable e1000e until the NVRAM corruption problem is found.
    - LP: #263555[/B]

  [ Upstream Kernel Changes ]

  * Revert "[Bluetooth] Eliminate checks for impossible conditions in IRQ
    handler"

Date: Tue, 23 Sep 2008 09:53:57 -0400
Changed-By: Ben Collins <ben.collins at canonical.com>
Maintainer: Ubuntu Kernel Team <kernel-team at lists.ubuntu.com>
Signed-By: Tim Gardner <tim.gardner at canonical.com>
[https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-4.6](https://launchpad.net/ubuntu/intrepid/+source/linux/2.6.27-4.6)


[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007475.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007475.html)


**How do I identify my Intel® Network Adapter and drivers?**


> **How to find your adapter driver version and device name in Linux***
Issue the following command to determine the version of the installed network adapter driver:
- ethtool -i <ethx>
<ethx> is the name of the ethernet device to query.
Use **ifconfig** to determine the device name




[http://support.intel.com/support/network/sb/cs-008441.htm](http://support.intel.com/support/network/sb/cs-008441.htm)


Example:  (running Realtek myself)
```

plun@plun:~$ **ethtool -i eth0**
driver: 8139too
version: 0.9.28
firmware-version: 
bus-info: 0000:00:0b.0
```

---

### Post by Scruffynerf on 2008-09-24
The scope may be larger than Intel Wired Ethernet systems. There is a report of a RealTek system being compromised, over at [http://lkml.org/lkml/2008/9/24/133](http://lkml.org/lkml/2008/9/24/133) with the same symptoms.

Seems to have hit the r8169 RealTek systems.

I've flagged that also in the Ubuntu Bugzilla, and there appears to be some cross-pollination at work.

---

### Post by jdong on 2008-09-24
If the reported root cause (some random spewing into the memory space by a crashing driver) is true, I wouldn't be surprised if more hardware is affected than just e1000e cards.

---

### Post by Gina on 2008-09-25
This looks really nasty :(

---

### Post by shellster on 2008-09-25
Well, chalk me up as one of those few that have been bitten by the bug.  I am using a Dell Optiplex 755.  According to lspci the onboard intel nic card is:  Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02).  Yesterday, after installing all the latest intrepid updates, and restarting the computer, the nic card ceased to function.  It still has lights on it, and flashes when an ethernet cable is plugged it.  It also, as mentioned above, still appears in lspci, but it does not seem to be picked up when I attempt to restart networking.  I ended up throwing an old 3Com Nic card into the box, and now I have my networking back at least.  To any developers, if you want to ask me any questions about this or have me provide more information, just ask.

---

### Post by shellster on 2008-09-25
Sorry for the double post but I should also mention:
The corrupted intel card used to be identified as eth0.  However, when I attempt to run "ethtool -i eth0" it says, "No such device".  So ethtool can't find it anymore.  Although I am unsure how one determines what number a NIC card will be assigned, I do know that the new 3Com card is recognized as eth1, which makes me think that something still recognizes that there is another NIC card in the computer.

---

### Post by mrinaldotnet on 2008-09-25
> **shellster said:**
> Well, chalk me up as one of those few that have been bitten by the bug.  I am using a Dell Optiplex 755.  According to lspci the onboard intel nic card is:  Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02).  Yesterday, after installing all the latest intrepid updates, and restarting the computer, the nic card ceased to function.  It still has lights on it, and flashes when an ethernet cable is plugged it.  It also, as mentioned above, still appears in lspci, but it does not seem to be picked up when I attempt to restart networking.  I ended up throwing an old 3Com Nic card into the box, and now I have my networking back at least.  To any developers, if you want to ask me any questions about this or have me provide more information, just ask.

Are you sure this is not simply because the e1000e module was blacklisted in yesterday's intrepid updates? The module will not get loaded and that's probably why your card doesn't work any more. (Check /etc/modprobe.d/blacklist-e1000e)

---

### Post by cwestpha on 2008-09-25
I have a Mac Pro (early 08') with a Intel 80003ES2LAN gigabit ethernet adaptor, which no longer works because of this blacklisting. I have tried explicitly enabeling e1000 and looking through the blacklists (cant find where its blacklisted) under modprobe.d to no avail.
Since workstation based chipsets appear to not be affected, is there anyways I can restore network conectivity?

---

### Post by shellster on 2008-09-25
Ah, that's what it is.  I did a search for the black list and found: 
/etc/modprobe.d/blacklist-e1000e

Thank you sir.

---

### Post by jrubens on 2008-09-25
How can i check if my loss of wired connections is due to the bug or the blacklist?

---

### Post by caryb on 2008-09-25
That would be a problem, If you un blacklist the E1000 module you run the risk if corrupting the NVRAM  it! I would use a old *buntu live cd (pre alpha 6) & boot to see if your network fires up (mine did) that way you know that your hardware is ok!


Cary

---

### Post by Neon Lights on 2008-09-25
Ignore, late post.

---

### Post by PmDematagoda on 2008-09-26
<redundant>

I would advise people interested in this problem or helping the developers out to keep an eye on the Linux Kernel mailing lists found [here]("http://lkml.org/") since that is where most of the action occurs. Granted that the lists are huge, however it is a gold mine for information related to the Linux kernel.

---

### Post by Scruffynerf on 2008-09-26
PmDematagoda - this is where my information is coming from, which I am distributing on various areas where I can (mainly here and Ars Technica, however my handle has appeared a couple of times in the Ubuntu Launchpad.

Edit: A summary of the issue currently appears at [http://lkml.org/lkml/2008/9/25/510](http://lkml.org/lkml/2008/9/25/510)

---

### Post by dabl on 2008-09-26
Just to add a data point:

I'm running Kubuntu II, fully updated, and my e1000e module got blacklisted in yesterday's update.  I'm about to unblacklist it, as there's been no sign of trouble while running the ~.27 kernels for the past few weeks.

Hardware (see signature):
> 
03:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller

---

### Post by PmDematagoda on 2008-09-26
> **Scruffynerf said:**
> PmDematagoda - this is where my information is coming from, which I am distributing on various areas where I can (mainly here and Ars Technica, however my handle has appeared a couple of times in the Ubuntu Launchpad.

Whoops, redundant data. Sorry about that.:oops:

---

### Post by Scruffynerf on 2008-09-26
> **PmDematagoda said:**
> Whoops, redundant data. Sorry about that.:oops:

No worries - it's good to know that there are a few people watching this now. I'm not a dev (don't even know how to code past SQL) and have no real input everywhere, I've just taken it upon myself to distribute info.

---

### Post by nanog on 2008-09-26
I have a box with this bug that is currently crippled. 

Does anyone have have a link to the 2.6.26-5 kernel, , image, headers, restricted-modules. I cannot find them in archive.ubuntu.com and I forgot to back up the packages. (Must remember to take periodic snapshots of /var/apt/cach/archives!)

---

### Post by plun on 2008-09-26
> **nanog said:**
> I have a box with this bug that is currently crippled. 

Does anyone have have a link to the 2.6.26-5 kernel, , image, headers, restricted-modules. I cannot find them in archive.ubuntu.com and I forgot to back up the packages. (Must remember to take periodic snapshots of /var/apt/cach/archives!)

Seems to be gone but the rt kernel probably works just fine

[http://packages.ubuntu.com/intrepid/linux-rt](http://packages.ubuntu.com/intrepid/linux-rt)

---

### Post by nanog on 2008-09-26
Plun, 
Thanks...I  was just going to post that the rt kernel works.

```

~$ uname -a
Linux tikal 2.6.26-1-rt #1 SMP PREEMPT RT Fri Aug 29 12:39:10 UTC 2008 x86_64 GNU/Linux

~$ dpkg -l | grep 2.6.26
ii  linux-headers-2.6.26-1-rt                  2.6.26-1.15                           Linux kernel headers for version 2.6.26 on Ingo Molnar'
ii  linux-headers-rt                           2.6.26.1.5                            Rt Linux kernel headers
ii  linux-image-2.6.26-1-rt                    2.6.26-1.15                           Linux kernel image for version 2.6.26 on Ingo Molnar's 

```

---

### Post by Scruffynerf on 2008-09-26
> **nanog said:**
> I have a box with this bug that is currently crippled. 

Does anyone have have a link to the 2.6.26-5 kernel, , image, headers, restricted-modules. I cannot find them in archive.ubuntu.com and I forgot to back up the packages. (Must remember to take periodic snapshots of /var/apt/cach/archives!)

Crippled because of the blacklisting, or crippled because of the bug?

If it because of the bug, it means that your ethernet firmware reads:
 ff ff ff ff ff ff

And nothing will make that work again, aside from possibly a BIOS reflash, although that has mixed results: working vs bricking

---

### Post by nanog on 2008-09-26
Scruffy, just blacklisting.

According to the posts on LKML intel is working on a utility that will allow reflashing of eeproms.

---

### Post by Amon_Re on 2008-09-27
Guys, i think you need to reword the title of this thread, i read this as a bug causing corruption of network traffic on these cards & not as a possible eeprom getting flushed.

I would replace corruption with bricking in the subject line.

---

### Post by jdong on 2008-09-27
> **Amon_Re said:**
> Guys, i think you need to reword the title of this thread, i read this as a bug causing corruption of network traffic on these cards & not as a possible eeprom getting flushed.

I would replace corruption with bricking in the subject line.
It does not "brick" the card. It only corrupts its NVRAM with invalid configuration options. I will reserve bricking as a term for actual irreversible firmware damage.

---

### Post by Arlanthir on 2008-09-28
The information on how to know if you're affected seems to be incomplete.

My eth0 info is:

```

driver: e100
version: 3.5.23-k4-NAPI
firmware-version: N/A
bus-info: 0000:08:08.0

```

Am I affected or does the "driver" field actually spell "e1000e" on those cards?

---

### Post by FuturePilot on 2008-09-28
> **Arlanthir said:**
> The information on how to know if you're affected seems to be incomplete.

My eth0 info is:

```

driver: e100
version: 3.5.23-k4-NAPI
firmware-version: N/A
bus-info: 0000:08:08.0

```

Am I affected or does the "driver" field actually spell "e1000e" on those cards?

I don't think so. It appears so far to only affect the Intel Gigabit cards that use the e1000e driver. What you have is not a Gigabit card. The Gigabit cards will say e1000e for the driver.

---

### Post by shafin on 2008-09-29
Thanks for the detailed helps.
I have kernel 2.6.27-2, am I affected? I dont currently use this card, so there is no way for me to know. I've just backup the eeprom, and it reads like this:

```
0x0000        00 17 31 52 3f d0 30 0b 46 f7 57 00 ff ff ff ff 
0x0010        ff ff ff ff 6b 02 c2 81 43 10 9a 10 86 80 df 80 
0x0020        00 00 00 20 54 7e 00 00 14 00 da 00 04 00 00 27 
0x0030        c9 6c 50 31 32 07 0b 04 84 29 00 00 00 f0 06 07 
0x0040        08 10 00 00 04 0f ff 7f 01 4d ff ff ff ff ff ff 
0x0050        14 00 1d 00 14 00 1d 00 af aa 1e 00 00 00 1d 00 
0x0060        00 01 00 40 1c 12 07 40 ff ff ff ff ff ff ff ff 
0x0070        ff ff ff ff ff ff ff ff ff ff ff ff ff ff 7f 1d 
```

---

### Post by dabl on 2008-09-29
2.6.27-2 boots and runs with ethernet working, for me.  2.6.27-4 has the module blacklisted -- no networking.

---

### Post by PGHammer on 2008-09-29
> **Arlanthir said:**
> The information on how to know if you're affected seems to be incomplete.

My eth0 info is:

```

driver: e100
version: 3.5.23-k4-NAPI
firmware-version: N/A
bus-info: 0000:08:08.0

```

Am I affected or does the "driver" field actually spell "e1000e" on those cards?

The affected NICs use the "e1000e" driver.  NOTE: Onboard Intel CSA uses the "e1000" driver and is NOT affected by this bug. (This also means that VirtualBox 2.x, with the optional Intel gigabit Ethernet configuration, is not affected.)  I have the ASUS P4C800E-Deluxe with onboard Intel CSA gigE (e1000 driver), and have no problems.

---

### Post by ubername on 2008-09-29
Hi 

I have marked the following thread as solved:

[http://ubuntuforums.org/showthread.php?t=931507](http://ubuntuforums.org/showthread.php?t=931507)

but I think it is exhibiting the same problem mentioned in this thread.

---

### Post by Delvien on 2008-09-30
After installing alpha6 from the repos, it "bricked" my ethernet temporarily. Logged into my dual boot Windows install, and it wasn't working. Uninstalled the driver, let it detect, and installed the driver again, a few reboots and it was working. 

After I installed Alpha6 is took down the port I was plugged into on my router, had to a reset of settings. (DD-WRT Linksys)

Not sure if this might be the/a issue.

---

### Post by jdong on 2008-09-30
Well apparently it can also set the MAC addy of the card to all FF's which might upset routers and switches somewhat :)

---

### Post by Delvien on 2008-09-30
> **jdong said:**
> Well apparently it can also set the MAC addy of the card to all FF's which might upset routers and switches somewhat :)

Weird....

---

### Post by xsilvergs on 2008-09-30
I'm not a tester and don't understand how my 8.04 got updated to Intrepid but after another update my wired networking has stopped. If I lspci I can see
03:00.0 Ethernet controller: Intel Corporation 82573V Gigabit Ethernet Controller (Copper) (rev 03)

uname -r gives 2.6.27-4-generic

If somebody can give an idiots guide to correcting my wired network I'd be grateful.

---

### Post by nanog on 2008-09-30
Windows apparently has the ability to reset the eeprom  -- at least to some degree.

The lack of progress is a bit disappointing. I wonder if this will be fixed in time for release.

---

### Post by nanog on 2008-09-30
> If somebody can give an idiots guide to correcting my wired network I'd be grateful.

```

sudo apt-get install linux-headers-2.6.26-1-rt linux-image-2.6.26-1-rt

boot into 2.6.26

if you run nvidia you may also have to reinstall nvidia-glx-177.68

```

---

### Post by xsilvergs on 2008-09-30
Thanks nanog. Will I have to manually select 2.6.26 each time or will it know to boot to it?

---

### Post by nanog on 2008-09-30
You can change your boot order in /boot/grub/menu.lst -- just be careful to back this file up before touching it.

---

### Post by jdong on 2008-09-30
Another incremental fix was committed today that only maps these vulnerable registers into memory when they are being written to by the driver, which should dramatically reduce the liklihook of corruption.

---

### Post by plun on 2008-10-01
2.6.27-RC8 is out and Linus T himself comments this

[http://lkml.org/lkml/2008/9/29/317](http://lkml.org/lkml/2008/9/29/317)


Please read all messages within the mailing list thread.


I am not a developer and I cannot comment this..... but for sure this
must be clarified.

---

### Post by Scruffynerf on 2008-10-01
I'm not a developer either, however it looks like Linus hasn't incorporated any of the patches into his tree, as what exactly is triggering the bug hasn't been nailed down, however in investigations to this, they have found some other issues. That said, as they have not been able to confidently reproduce the issue, they haven't been able to fix it as yet.

Linus seems to think that it could be either a fully firmware problem (Intel's bag) or an X Server issue (whoever maintains that system's bag)... which is fair enough from his standpoint.

---

### Post by jdong on 2008-10-01
Well, this is Linux, fortunately -- we don't NEED Linus to incorporate anything into his tree per se. Our distributed model of development works well for situations like this where we have to diverge from the main tree.

---

### Post by nanog on 2008-10-01
So where is the fix? Is there a patch or a patched kernel built yet? I'd be willing to test just about anything at this point.

---

### Post by nanog on 2008-10-01
[http://lkml.org/lkml/2008/9/29/384](http://lkml.org/lkml/2008/9/29/384)
[http://lkml.org/lkml/2008/9/30/29](http://lkml.org/lkml/2008/9/30/29)

Some progress on this thread.

---

### Post by plun on 2008-10-01
> **nanog said:**
> So where is the fix? Is there a patch or a patched kernel built yet? I'd be willing to test just about anything at this point.

You can "lurk" Ubuntus GIT....:D

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-intrepid.git;a=summary)

Its "beta vacuum" also for the moment...

---

### Post by xsilvergs on 2008-10-01
As this is only the second go at ubuntu what I don't understand is; With the previous Kernel I could set up my network settings in /etc/network/interfaces with IP, network mask etc. With this latest Kernel it makes no difference what is written, the file can be blank.

The only way of setting things is by right clicking the network icon at the top of the screen, selecting Edit Connections, choosing the relevant network and clicking the IPv4 Settings tab and adding the desired info. Not everything stays as typed, Network changes back from 255.255.255.0 to 24 when view later.

Today I've added a PCI network card, in the hope that this may allow me wired networking. It still doesn't work!

---

### Post by caryb on 2008-10-01
When I added a 2nd nic I had to edit the interfaces file & make reference to eth1 i.e.
> 
 The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp


Cary

---

### Post by xsilvergs on 2008-10-02
@ caryb

It doesn't matter what I put in my network file be it blank or with eth0 or eth1 it's as though it's being ignored. This has only changed since the last Kernel change.

---

### Post by plun on 2008-10-02
"Fwiw"

This is probably because of several bugs... kernel and network apps

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bugs)

The first one seems to mess up everything.  (Samba sharing is "out of order for me) 

I dont understand this...

> [keyfile]
hostname=YOURHOSTNAME

to /etc/NetworkManager/nm-system-settings.conf when using the keyfile plugin.

What keyfile ???

---

### Post by Scruffynerf on 2008-10-02
Can we keep to the topic please? Other unrelated issues need their own threads please.

On Topic:

It looks like the clever people at Intel have a fix that will lock the memory registers for the NVM issue. They are pushing for the lock to go in 2.6.27, with other patches ready for 2.6.28 to complement it.

More info at: [http://lkml.org/lkml/2008/10/1/368](http://lkml.org/lkml/2008/10/1/368)

---

### Post by nanog on 2008-10-02
Looks like one of the intel patches "fixes" the overwrite:

[http://lkml.org/lkml/2008/10/2/121](http://lkml.org/lkml/2008/10/2/121)

Added to 2.6.27

[http://lkml.org/lkml/2008/10/1/379](http://lkml.org/lkml/2008/10/1/379)

---

### Post by Kow on 2008-10-02
> **nanog said:**
> Looks like one of the intel patches "fixes" the overwrite:

[http://lkml.org/lkml/2008/10/2/121](http://lkml.org/lkml/2008/10/2/121)

Added to 2.6.27

[http://lkml.org/lkml/2008/10/1/379](http://lkml.org/lkml/2008/10/1/379)

I sense a new intrepid kernel release coming soon. I'm guessing the beta may be delayed until this patch gets in.... however kernel rebuilds are a touchy issue.

---

### Post by dabl on 2008-10-02
Says here, in "Known Issues" that the next daily build will include the patch:

[https://wiki.ubuntu.com/IntrepidIbex/TechnicalOverview#Known%20Issues](https://wiki.ubuntu.com/IntrepidIbex/TechnicalOverview#Known%20Issues)



May I add .... Hooray!  :guitar:

---

### Post by BCurtisWX on 2008-10-02
yup, its in the builds.. 2.6.27-5.8

---

### Post by nanog on 2008-10-02
According to the bug report its 2.6.27-4.7.

---

### Post by plun on 2008-10-03
[https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007852.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-October/007852.html)

> linux (2.6.27-5.8 ) intrepid; urgency=low

<>

* Enabled CONFIG_E1000E, disabled CONFIG_E1000E_NEW
    This takes advantage of the upstream NVM protection fix in
    commit 4a7703582836f55a1cbad0e2c1c6ebbee3f9b3a7.

* e1000e: write protect ICHx NVM to prevent malicious write/erase

<>

---

### Post by jsob on 2008-10-03
Hi,

I am new to Ubuntu, and am trying to install Intrepid on an Intel DG45FC motherboard with the NIC problem.

I am having trouble finding the "daily build" that has the patch applied and allows me to use my NIC.  Can someone help me find the iso file itself (Desktop X86 Live)?

Alternatively, I have 8.10 beta that was just realeased downloaded and installed, but my NIC is disabled.  Can someone walk me through the commands to enable the NIC?

I think I need to enable the e1000e driver, and then it should recognize my NIC?  Or, do I have to find the "daily download" that does not have my NIC disabled?

Thank you very much.

-John

---

### Post by jdong on 2008-10-03
Daily images may be found at [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/)

Note you want one dated AFTER the beta (none available yet). If your NIC isn't automatically enabled, please don't force it enabled or you might be forcing Ubuntu to expose your system to this bug :)

---

### Post by paulm on 2008-10-03
Is there an idiots guide to re enabling ethernet so I can get the updates? I tried deleting the blacklist file, but that didn't seem to do anything.

Edit: Or perhaps it did. My mistake.

---

### Post by Taxman415a on 2008-10-04
The first daily image for Oct 4 is out and it still has linux-generic 2.6.27.4.4. So the kernel hasn't yet been updated to what was noted above as the needed 2.6.27-5.8 in this daily build. So wait until tomorrow at least.

Ed, check the kernel package version in the manifest file 
[http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-amd64.manifest](http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-amd64.manifest)
or
[http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.manifest](http://cdimage.ubuntu.com/daily-live/current/intrepid-desktop-i386.manifest)

after first looking here
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)
to see if a new daily version is out. Then in the manifest file look for the version of the linux-generic package.

---

### Post by WiFi Ed on 2008-10-04
> **Taxman415a said:**
> The first daily image for Oct 4 is out and it still has linux-generic 2.6.27.4.4. So the kernel hasn't yet been updated to what was noted above as the needed 2.6.27-5.8 in this daily build. So wait until tomorrow at least.

I need to get the patched kernel so I can try Intrepid Ibex out. Can I find out somewhere what kernel is in the daily build without installing it first?

---

### Post by nanog on 2008-10-04
The kernel is now available but does not automatically get installed as an upgrade or dist-upgrade. Install the kernel, headers, headers-generic, and restricted modules from the cli or synaptic.

Direct links for those who do not have a functional network card in linux:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-libc-dev](http://packages.ubuntu.com/intrepid/linux-libc-dev)

---

### Post by WiFi Ed on 2008-10-04
> **nanog said:**
> The kernel is now available but does not automatically get installed as an upgrade or dist-upgrade. Install the kernel, headers, headers-generic, and restricted modules from the cli or synaptic.

Direct links for those who do not have a functional network card in linux:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5-generic)

[http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-5-generic)

Ok, that seems to have worked. Thanks! I downloaded the 4 packages, installed Ibex beta and then installed the 4 packages. Ethernet now works in Ibex!

Can't get the nvidia restricted driver to install though. Maybe I didn't install the kernel packages correctly? I'll do a fresh install with the new daily build tomorrow and see if that fixes it.

---

### Post by nanog on 2008-10-04
i have tried nvidia 173 and 177. they dkmsed fine during kernel upgrade and also install via jockey.

plun suggested that linux-libc-dev might be missing and i added it to my set of links in the previous post

---

### Post by WiFi Ed on 2008-10-04
Thanks nanog, I'll try linux-libc-dev...:-)

---

### Post by fitzman49 on 2008-10-04
For those who have another network connection on their computer, it looks like the 2.6.27-5 kernels are in the repositories.  Make sure you have the proposed and back ports updates turned on. Then just run the following:

```
sudo apt-get install linux-image-2.6.27-5-generic
```

If you are afraid of the CLI, you can also find that package in synaptic too.

---

### Post by caryb on 2008-10-05
Thanks fitzman49 I now have e1000 & sound back as a bonus after kernel upgrade:D

Cary

BTW you have to edit /etc/modprobe.d/blacklist & # out the e1000 entry for the driver to load.

Cary

---

### Post by Mr Fredrick on 2008-10-05
> **nanog said:**
> The kernel is now available but does not automatically get installed as an upgrade or dist-upgrade. Install the kernel, headers, headers-generic, and restricted modules from the cli or synaptic.

Direct links for those who do not have a functional network card in linux:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-5-generic)

[http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-5-generic)

[http://packages.ubuntu.com/intrepid/linux-libc-dev](http://packages.ubuntu.com/intrepid/linux-libc-dev)

If I were to install these packages from a CLI exactly what command would I enter at the prompt.

Thanks,

Mr Fred

---

### Post by plun on 2008-10-05
> **Mr Fredrick said:**
> If I were to install these packages from a CLI exactly what command would I enter at the prompt.

Thanks,

Mr Fred

```
sudo apt-get install linux-libc-dev linux-headers-2.6.27-5 linux-headers-2.6.27-5-generic linux-restricted-modules-2.6.27-5-generic linux-image-2.6.27-5-generic

```

-----------------

If you have downloaded deb packages with another PC its just to double click on a deb-file and Debians installer starts.

You can download each package as a deb file with another PC and then transfer all files to the PC with a broken kernel.  A burned CD, USB stick etc can then be used.

---

### Post by EnGorDiaz on 2008-10-05
> **shellster said:**
> Well, chalk me up as one of those few that have been bitten by the bug.  I am using a Dell Optiplex 755.  According to lspci the onboard intel nic card is:  Ethernet controller: Intel Corporation 82566DM-2 Gigabit Network Connection (rev 02).  Yesterday, after installing all the latest intrepid updates, and restarting the computer, the nic card ceased to function.  It still has lights on it, and flashes when an ethernet cable is plugged it.  It also, as mentioned above, still appears in lspci, but it does not seem to be picked up when I attempt to restart networking.  I ended up throwing an old 3Com Nic card into the box, and now I have my networking back at least.  To any developers, if you want to ask me any questions about this or have me provide more information, just ask.

hey wait i had this problem on 8.04 

i just got a new network card that fixed it...

:( though it peeved me off

---

### Post by Fischli on 2008-10-05
Shouldn't the new kernel be in the daily CD images?

I looked through [http://cdimage.ubuntu.com/daily/20081005/intrepid-alternate-amd64.list]("http://cdimage.ubuntu.com/daily/20081005/intrepid-alternate-amd64.list") but was only able to find 
```
linux-image-generic_2.6.27.4.4_amd64.deb

```
in there but not the new 2.6.27.5.

Does anybody know when the new kernel will be in the daily CD images (cause I'd like to use one of these).

Thanks!

---

### Post by derubermensch on 2008-10-05
I'd like to know as well when the Daily Live images will be updated.

---

### Post by dabl on 2008-10-05
As of the 5 OCT 08 daily build, it's still 2.6.27-4.  :(

However, if you're stuck with no network and looking for a fast way out, here's what I did.  (I assume you have another OS or PC to use for the downloads.)

First, grab the daily build ISO for your arch from [**[COLOR="Green"]here[/COLOR]**](http://cdimage.ubuntu.com/) and install it.  Then get the packaged 2.6.27-5 kernel image from here:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-5-generic)

Save it on a USB stick or something.

Boot your 8.10 system (daily build) which of course has no ethernet, copy the deb into /tmp, and use gdebi to install it.  In my first attempt, gdebi threw up an error from parsing the /etc/apt/sources.list file, so I commented out all the sources and tried again.  Second attempt, gdebi asked if I really intended to force the kernel installation, and I answered "yes", and it went through the complete installation process including modification of the /boot/grub/menu.lst file.

Upon reboot, I had my 2.6.27-5 kernel, and ethernet.  I then un-commented the sources in /etc/apt/sources.list, and ran sudo apt-get update & upgrade and also got the kernel header files, and with that I was able to install the new Nvidia 177.78 driver on the new kernel, set up my desktop, and now it's a fully functional Intrepid Ibex system.  Compiz works (with Alt-F2 still functional), Firefox works with flash, etc. etc. -- looking very good here!

  :guitar:

---

### Post by nanog on 2008-10-05
First of all, a nonfuntional e1000e card does not mean you are affected by the bug. The driver was disabled in intrepid and is only reactivated in the new kernel. If you still think you've been affected run the following command:
```
sudo ethtool -e eth0 > savemyeep.txt; nano savemydeep.txt
```
**you have been affected only if your eeprom contains nothing but FF**
 

Secondly, this bug **does not affect Hardy**.


Thirdly, it does not affect all e1000e cards **only the subset that have the ICH8 and ICH9 intel chipset**.



Finally, the new kernel is available via the repos -- just upgrade -- or download from the links I provided here:

[http://ubuntuforums.org/showpost.php?p=5907023&postcount=64](http://ubuntuforums.org/showpost.php?p=5907023&postcount=64)
you have to click the link for your architecture and then install by right click gdebi or dpkg -i from the command line.

---

### Post by Taxman415a on 2008-10-06
Ok, according to the October 6 manifest file the kernel has been updated to version 2.6.27-5.8, so the latest daily has the patched kernel now.

---

### Post by Sef on 2008-10-06
> Ok, according to the October 6 manifest file the kernel has been updated to version 2.6.27-5.8, so the latest daily has the patched kernel now.


That kernel is being installed on my computer now.

---

### Post by Gina on 2008-10-07
It came down today with a number of other updates with Updaate Manager :)

---

### Post by shellster on 2008-10-08
I'm a little late on the scene here, but the update came down I believe Friday of last week, and since then my old intel NIC has been working flawlessly.

---

### Post by rondackcpu on 2008-10-08
Did I misunderstand things here?  I just downloaded and burned the 8-October daily build.  When it boots, the Intel NIC (e1000e) is disabled.

Is there something else going on?

Thanks.

CRS

---

### Post by shellster on 2008-10-08
I don't know what to tell you.  If you can, I suggest, putting in another NIC card, and then installing all the latest updates.  In my case, the fix came down the pipe as an update.  One would hope that it is in the daily build, but it might not be.

Search for 'blacklist' on your computer, and see if you come up with one that says something like blacklist-e1000e.  If you do, the driver is still being blacklisted, and you don't have the latest fix.

---

### Post by bdash on 2008-10-08
I looked with ethtool and in Hardy the driver says "e1000". Does that mean my card would be using the dangerous e1000e on Intrepid, or it is safe for me to updgrade?

---

### Post by dabl on 2008-10-08
Just boot a 8.10 Live CD, and try it.  [COLOR="Magenta"]**Get the daily build ISO, not the Beta**[/COLOR] (with the e1000e blacklisted).  If it runs correctly in Live CD mode, then there's not a reason to fear it when installed.

---

### Post by fendora on 2008-10-09
$ uname -a
Linux thinkbuntu 2.6.27-6-generic #1 SMP Tue Oct 7 04:15:04 UTC 2008 i686 GNU/Linux

$sudo modprobe -r e1000e
$sudo modprobe e1000e

Oct 10 09:30:23 thinkbuntu kernel: [ 2014.511504] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.511521] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.516340] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.516379] e1000e 0000:00:19.0: setting latency timer to 64
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.564137] 0000:00:19.0: 0000:00:19.0: The NVM Checksum Is Not Valid
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.576945] e1000e 0000:00:19.0: PCI INT A disabled
Oct 10 09:30:23 thinkbuntu kernel: [ 2014.578814] e1000e: probe of 0000:00:19.0 failed with error -5

i've already upgrade to the latest kernel but seem it not fixed mine. do anyone know what else i should do ?

---

### Post by dondad on 2008-10-10
I have the beta for intrepid installed, and it looks like I have the card that is blacklisted. My question is how do I fix it when the correction comes out with no network connection? I do have a working Gutsy installation on a different drive on the same machine.

---

### Post by caryb on 2008-10-11
This has been fixed for about a week now, If your packages are up to date & you have a kernel version of 2.6.27-5 or higher at a terminal type "uname -a" it is fixed, from there from the terminal type "nano /etc/modprobe.d/blacklist" you will see a line with e1000 just put a # in the front of it to comment it out. Then reboot & all should be good. If your not confident with your editing skills just run "cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.sav



Cary

---

### Post by dondad on 2008-10-11
> **caryb said:**
> This has been fixed for about a week now, If your packages are up to date & you have a kernel version of 2.6.27-5 or higher at a terminal type "uname -a" it is fixed, from there from the terminal type "nano /etc/modprobe.d/blacklist" you will see a line with e1000 just put a # in the front of it to comment it out. Then reboot & all should be good. If your not confident with your editing skills just run "cp /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.sav



Cary
I have 2.6.27-4. I can't update because I can't connect to the internet ;-) I haven't done anything with it yet, so I figured it might be easiest to just download the daily and reinstall, but when I get that iso and try to reinstall, it gets to the partitioner and then hangs when I try to select manual partitioning. (I have /home on another partition and do not want to format it)
I do have a functioning install of hardy, so could download something there and move it over to the intrepid drive. I guess what I need to find out is either how to get it past the partitioner, or what I can download to fix it in my hardy install. Thanks for any help you can give.

I did check the daily cd for integrity and burned it at a slow speed. It checks out fine.

---

### Post by rondackcpu on 2008-10-11
There are a lot of things in this world that I do not understand.  This e1000e thing is only one of them.  

Like Dondad, above, I downloaded and burned the daily build for 8-Oct.  On my machine, it installs just fine, except that networking is unavailable.  It has kernel 2.6.27-6.  My machine has the Intel e1000e wired ethernet controller.

As per the above suggestion, I looked in /etc/modprobe.d/blacklist, but there is no mention of e1000 or e1000e.

My machine has a second NIC.  One of the Broadcom wireless ones which I can usually get working by a plan set out long ago by fellow poster "Mazza".  Following that plan does not result in a connection to the Internet.

It seems as though all of Networking is disabled.  Yet many others here are posting that they have overcome the problem.  What is missing?

Any other suggestions?

CRS

---

### Post by nanog on 2008-10-11
dondad,
i've updated links to the packages here:

[http://ubuntuforums.org/showpost.php?p=5907023&postcount=64](http://ubuntuforums.org/showpost.php?p=5907023&postcount=64)

you need to scroll down and choose the appropriate package (i386 or x64)

the package can be installed by right clicking and using gdebi or by cding to the directory and using dpkg -i packagename. (they will uninstall and update normally)

if the links don't work replace the 7 with an 8. (i think there will be a new kernel soon.)



----------------------------------------------------------------

rondackcpu,
you have another problem and may want to file a bug. its also possible your /etc/network/interface file is borked -- post it here.

---

### Post by dondad on 2008-10-12
> **nanog said:**
> The kernel is now available but does not automatically get installed as an upgrade or dist-upgrade. Install the kernel, headers, headers-generic, and restricted modules from the cli or synaptic.

Direct links for those who do not have a functional network card in linux:

[http://packages.ubuntu.com/intrepid/linux-image-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-image-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7)

[http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-headers-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-restricted-modules-2.6.27-7-generic)

[http://packages.ubuntu.com/intrepid/linux-libc-dev](http://packages.ubuntu.com/intrepid/linux-libc-dev)

Thank you! That got me connectivity so that I could get all the updates and start trying to get everything working ;-)

---

### Post by Roasted on 2008-10-14
I've read several threads, and I hate to sound like an idiot but I just have to ask.

What "exactly" happens when these network cards get corrupt, in plain english? Do they not work? Do they blow out the board? Are they fixable? Are you forced to get a PCI LAN card? Is the motherboard left completely intact and functional?

Can we expect the final release of Intrepid to fix this issue?

Is it often that we get issues like this with distros in the beta stage?

---

### Post by jdong on 2008-10-14
> **Roasted said:**
> I've read several threads, and I hate to sound like an idiot but I just have to ask.

What "exactly" happens when these network cards get corrupt, in plain english? Do they not work? Do they blow out the board? Are they fixable? Are you forced to get a PCI LAN card? Is the motherboard left completely intact and functional?


The nonvolatile RAM (like flash) that stores settings and parameters such as the MAC address is overwritten with garbage, and the card is basically as if you flashed something with nonsense firmware. The drivers do not communicate with the card, and cannot bring the NIC online because of inconsistent/invalid data. There is no physical damage or hazard to safety.


Whether or not it's reversible is unknown. Some say a BIOS flash will fix it. For systems without BIOS flashes available, there will be a tool to restore the nvram from a backup. For people who didn't back up, I have no idea.

> 
Can we expect the final release of Intrepid to fix this issue?

Is it often that we get issues like this with distros in the beta stage?

yes, the final version of Intrepid (in fact the daily builds right now) have a fix that locks these areas of the memory after the card is initialized. This is no longer a problem.

It is not often for buggy operating systems to damage the hardware. The design of this particular Intel hardware has been widely criticized in the community by well-respected developers for its irresponsible exposure of sensitive areas of the device to accidental damage.

---

### Post by bigbear2350 on 2008-10-14
thats why I go with AMD.

---

### Post by jdong on 2008-10-14
> **bigbear2350 said:**
> thats why I go with AMD.

What does that have to do with anything in this thread?

---

### Post by ssam on 2008-10-16
The root cause of the problem has now been found and fixed.
[http://lwn.net/Articles/303390/](http://lwn.net/Articles/303390/)

---

### Post by Simplicius on 2008-10-17
> rondackcpu,
you have another problem and may want to file a bug. its also possible your /etc/network/interface file is borked -- post it here.

Well I'm not rondackcpu but I have the same problem. I'm asking here because I'm unsure about forums etiquette and whether I should open a new thread. My ethernet works fine in Hardy but with today's (October 17th) Intrepid it doesn't. 

My /etc/network/interface file is completely empty.

Thanks for any suggestions!!

---

### Post by jdong on 2008-10-17
Please start separate threads with networking issues unless you are sure it's related to this particular bug. Thanks!

---

### Post by jbrandeb on 2008-10-17
I would like to offer assistance to people who have had issues with their NVM being corrupted.  This would only apply to people running e1000e and a 2.6.27-rc1 or newer kernel.

If you're getting the "NVM is corrupted" message please let me know.  Maybe private IMs are best and then I can develop the set of possible eeprom images, etc that we may need.

when you reply please include 
a) your previous `ethtool -e ethX` dump (if you had it before it got corrupted)
b) your motherboard vendor and model number (and bios version if possible)
c) your current `lspci` output

---

### Post by forcecore on 2008-10-19
But why intel use writable flash chip that can be damaged, why they not use fixed read only chips?

---

### Post by cprofitt on 2008-10-19
Will 8.10 release with the 2.6.27.1 Kernel w/ the permanent fix or some variant of 2.6.27 w/ a patch?

---

### Post by jdong on 2008-10-19
> **forcecore said:**
> But why intel use writable flash chip that can be damaged, why they not use fixed read only chips?

Because it allows parameters to be changed and saved over reboots. In addition, most devices these days use writeable flash chips even for their firmware.

---

### Post by Gina on 2008-10-19
And it allows the firmware to be updated, of course.  Bugs can be corrected etc.

---

### Post by bigbear2350 on 2008-10-20
AMD=Smarter choice
Intel=Bugs+corruptions

---

### Post by Cauda_Draconis on 2008-10-24
So it *is* confirmed that Ibex will no longer brick/corrupt one's network card?

---

### Post by jdong on 2008-10-24
> **Cauda_Draconis said:**
> So it *is* confirmed that Ibex will no longer brick/corrupt one's network card?

Correct. This issue is resolved.

---

### Post by drunken_sapo on 2008-10-26
I think I have installed the last updates. My current kernel version is:
Linux laia 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
Is this bug corrected in this version?
Thank you very much.

---

### Post by wizard10000 on 2008-10-27
> **Cauda_Draconis said:**
> So it *is* confirmed that Ibex will no longer brick/corrupt one's network card?

Redundant, but it didn't brick mine.  Embedded e1000 in a Dell Precision 360.

---

### Post by drunken_sapo on 2008-10-29
> **drunken_sapo said:**
> I think I have installed the last updates. My current kernel version is:
Linux laia 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux
Is this bug corrected in this version?
Thank you very much.

Well, any hints before i roll back to hardy? Everywhere around people is saying that bug is corrected. But I still have no wired network.
Thanks in advance.

---

### Post by jdong on 2008-10-29
Yes, this bug is corrected in that kernel release. Can you try the LiveCD for the RC and see if the problem persists?

---

### Post by drunken_sapo on 2008-10-29
> **jdong said:**
> Yes, this bug is corrected in that kernel release. Can you try the LiveCD for the RC and see if the problem persists?

Yes I do. I will report it asap. Maybe the problem is that I've updated from hardy. I will try with live CD and after that a fresh install.
Thank you.

---

### Post by themtx on 2008-10-29
10/3 RC LiveCD did not allow wired networking on my Dell Optiplex 755 w/e1000e

10/27 RC LiveCD wired networking worked as expected, so did the clean install I just completed a short while ago (spare disk I had lying around).

I think I'll attempt an upgrade from Hardy tomorrow...

---

### Post by katon on 2008-10-29
i don't understand .... is this the driver?
[http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=3003&DwnldID=15817&agr=Y&lang=eng&PrdMap=3003](http://downloadcenter.intel.com/Detail_Desc.aspx?strState=LIVE&ProductID=3003&DwnldID=15817&agr=Y&lang=eng&PrdMap=3003)

is from 28/10/2008

is already in intrepid?

---

