---
title: "Ubuntu 8.04 with Marvell Yukon 88E8040T"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by ombos on 2008-05-03
I installed Ubuntu 8.04 on my laptop which has Marvell Yukon 88E8040T network controller (wired LAN). It seems neither sky2 not skge driver works.
Tried to download driver from Marvell website, the install.sh doesn't work at all (after changing to bash).
Now I am swamped, did anybody have the same experiences, please help!
Thank you.
BTW, lspci snippet below:
...
07:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4355 (rev 12)
...

---

### Post by jeanbaptiste on 2008-05-27
Hello,
I had the same problem and just fixed it.
You have to install the ubuntu kernel sources (package 'linux-source'). After extracting the archive which is in the '/usr/src' directory, you have to modify the 'skge.c' file which is in the 'driver/net/' subdirectory. You have to add the following line :
{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) },
in the table named 'skge_id_table' (around line 80). Then compile and install the kernel and its modules... it should work.
Hope it was clear enough.

Jean-Baptiste

Edit : I did a mistake on the file to modify. See next post to know which one you have to modify.

---

### Post by jeanbaptiste on 2008-05-27
Sorry I did a mistake... it isn't the 'skge.c' file you have to modify. You have to add the following line :
{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) }, /* 88E8040 */
in the 'sky2.c' file (same directory).
You should add it in the table named 'sky2_id_table' which starts around line 102.
The skge modification resulting from attempt to solve my problem and didn't work.
Sorry again.

Jean-Baptiste

---

### Post by pmasereeuw on 2008-06-05
Jean-Baptise -

Thank you - it worked.

Your explanation, albeit clear, was rather terse, so I will describe into somewhat more detail what I did to get it going. I am not familiar with kernel building and things related, and I figure there are more people like me. Anybody who wants to comment on my doings, please feel free.

I used the following page for information about building a kernel:

	[https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile")

First, I followed the instructions to make sure that the right tools were installed:

	```
sudo apt-get install linux-kernel-devel fakeroot build-essential
```

Then I obtained the most recent kernel source using git, which must be installed first:

	```
sudo apt-get install git-core
```

After installing git, I did:

	```
git clone git://kernel.ubuntu.com/ubuntu/ubuntu-hardy.git ubuntu-hardy
```

and

	```
git pull
```

which did not seem to be needed.

Than I changed into the directory with the sources (in my home directory):

	```
cd ~/ubuntu-hardy/
```

and modified the code according to your instructions:

	```
gedit drivers/net/sky2.c
```

Navigated to line 122 and inserted jeanbaptiste's addition after it (note that I changed the comment - 0x4354 is alreay there and has 88E8040 as comment (without T). I made sure to insert the line at the right place, between 0x4354 and 0x4356 because I don't know if the table is supposed to be sorted.

	```
{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) }, /* 88E8040T */
```

After that I compiled the kernel, but than I found out that the default procedure builds all possible flavours, so I stopped it and instead issued the command:

	```
AUTOBUILD=1 fakeroot debian/rules binary-debs flavours=generic
```
which I found here:

	[http://ubuntuforums.org/showthread.php?t=607797]("http://ubuntuforums.org/showthread.php?t=607797")

After the build was ready, there were several *.deb files in the parent directory of ubuntu-hardy. Using nautilus, I double-clicked on:

	```
linux-image-2.6.24-19-generic_2.6.24-19.33_i386.deb
```

and ignored the message "You likely do not want to install this package directly."

After that, I rebooted, choose my new kernel from the grub list and found that I had a /dev/eth0.

I also found out that my sound is not working anymore, but I can live with that. I hope jeanbaptiste's patch will make it soon to the official ubuntu kernel.

---

### Post by sophie27 on 2008-06-20
Hi guys, I've found your posts very interesting 'cause I have the some problem with Marvell (I've got a Toshiba A300 laptop with Kubuntu 8.04).

I've tried to use Marvell Drivers but I can't install them (It says there's a mismatch between linux kernel  and headers :confused:)

I'm a newbie and I can't connect to internet, for these reasons I'd prefer to avoid to compile-install kernel way. 
It would so long to me manually install all the necessary packages and also I'm not sure to be able to ...not damage the kernel!

My question is: is there any other way to make my ethernet card work?
Is there any other suitable driver for Marvell Yukon 88=8040T

Thank you so much

---

### Post by jeanbaptiste on 2008-06-20
@ pmasereeuw :
> I also found out that my sound is not working anymore, but I can live with that. I hope jeanbaptiste's patch will make it soon to the official ubuntu kernel.

I had the same problem. If you have the same audio chip than me, you just have to add the Intel HDA driver in your kernel (SND_HDA_INTEL flag).

@ sophie27 :
Sorry but the only way I have found to allow the 88E8040T to work was to rebuild my kernel with the patch. Maybe the next Ubuntu kernel will include the patched driver...


Jean-Baptiste

---

### Post by pmasereeuw on 2008-06-22
HI Jean-Baptise,

Never mind the sound. I don't use it when I need the wired connection, because that's in the office.

I just redid your guidelines for the new official kernel (2.6.24-20) and it still works.

I am just wondering if you or I could help sophie27 by sending her the *.deb packages that come from the compilation. I have no other experience with home-compiled kernels, so I don't know if this would bring her into other troubles. Perhaps you could give your opinion as the expert...

Best,

Pieter

---

### Post by jeanbaptiste on 2008-06-22
Hi,

Thank you Pieter for the redirection on the kernel list.

Sophie27, I will try do build a kernel package for you, but I'm not used to do kernel package... it may take few days to do so. 
By the way I would like to warn you about the potential risk to install a kernel package (and by extension any other package) which come from any non-official source. Some people may introduce malicious code in those packages.
To build the kernel I need to know what sort of processor you have (32 or 64 bit).

Jean-Baptiste

---

### Post by Koalasa on 2008-06-25
I have the same problem : I recently bought a Toshiba Satellite P300 laptop, and have installed Ubuntu on it. But Ubuntu doesn't find the Ethernet controller (a Marvell Yukon 88E8040T too). But my Internet connexion passes through this Ethernet Controller. So, I can't go and find packages ... Thank for your help !

---

### Post by sophie27 on 2008-06-26
Hi!
Some other friend suggest me to wait for the next Ubuntu kernel...
However It could be interesting to try with you kernel package, jeanbaptiste!
If you can do it, It would be great.(
My processor is 64 bit.)
But which are exaclty the risks in installing that? I mean, if the worst risk is that my ubuntu has to be reinstalled, it is ok; if there's the risk I all my computer, maybe it would be better to wait...


thanx so much!

---

### Post by allinitis on 2008-06-26
Hello, 

I have the same issue with a Toshiba A300D Amd64, running Ubuntu Hardy Heron and I believe the same Marvell adapter.  I am a complete Novice regarding Linux and in a similarly isolated position as far as the internet goes.  This maybe a stupid question but is there any way of performing the steps outlined by pmasereeuw without an internet connection on that machine?  

Thanks

Allinitis

---

### Post by sophie27 on 2008-06-27
mmmm it seems quite hard to perform it without a connection.

I don't have a connection and when I want to install a package I download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and it is ok (even if quite long, because you have to pay attention to dependencies! so you have to download several packages each time).

But even if you get the packages in this way (ex: git-core), then how can you  perform the following functions (ex: git clone git etc...)??

I wait for your opinions...

---

### Post by wanted on 2008-06-28
Hi, I've found a simpler solution than recompiling the kernel, which is simply to patch the binary driver. See the bug #239852 in launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/239852](https://bugs.launchpad.net/ubuntu/+bug/239852)

---

### Post by Koalasa on 2008-06-29
Thank you. My problem is that I am really a beginner and I don't understand anything to what is a kernel and a binary driver ... Taht makes it much harder to rebuild, patch or so. Can anyone explain me how to make it step by step ? Tank you.

---

### Post by wanted on 2008-06-29
OK, I hope the following instructions should help. All you need to do is to open a terminal and copy-paste the following commands.

```
$ sudo su -
[type your password]
# rmmod sky2
# cd /lib/modules/`uname -r`/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
# echo sky2 >> /etc/modules
# modprobe sky2

```
The last command loads the fixed driver and you should see it detect your network card like this:
$  dmesg | grep sky2
[   30.364735] sky2 0000:07:00.0: v1.20 addr 0x88000000 irq 17 Yukon-FE+ (0xb8) rev 0
[   30.365174] sky2 eth0: addr 00:1e:68:46:d3:34
[   33.962661] sky2 eth0: enabling interface

On next reboot, the driver should load automatically, so all you need to do is to configure the network parameters then.

Obviously, when you upgrade your kernel (e.g. via Synaptic) you should repeat all the commands up to the "perl" line.

HTH.

---

### Post by Koalasa on 2008-06-29
Tank you that worked. I now can browse on the Internet using my ethernet controller.

---

### Post by sophie27 on 2008-06-30
Thank you, wanted, I'm gonna try you solution!


Actually, I've succeeded in compiling a new kernel (read my last post in:
[http://ubuntuforums.org/showthread.php?t=816413](http://ubuntuforums.org/showthread.php?t=816413)) but, t**he new kernel...does not work (kernel panic!)** and I don't understand why (i suppose there's some problem in configuration...)

Anyway, your solution sounds good ...
I'll tell you...

---

### Post by sophie27 on 2008-06-30
A little problem: when I do "rmmod sky2" i get this error:

**ERROR: Module sky2 does not exist in /proc/modules.**

:confused: 

(I have KUBUNTU 8.04)

---

### Post by sophie27 on 2008-06-30
Ok, I've done it (doing modprobe sky2 before all)!
Now I can see my connection, **THANK YOU SO MUCH, WANTED.**:)

I don't want to bother you, but just to understand better: can you explain
more in details (or tell me where I can get explanations about that) the meaning of the commands:

# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko

i mean, i understand that the first is to copy and to second to modify sky2, but i would like to understand them better.

Thank you again, have a good day

---

### Post by wanted on 2008-06-30
Yeah, rmmod was just in case you already have the module loaded in memory, but if that's not the case, then rmmod will show a harmless error message.

The "cp -p sky2.ko{,.orig}" is equivalent to "cp -p sky2.ko sky2.ko.orig", just using shell expansion for brevity. More info in "man bash", topic "Brace Expansion".

In perl I'm using the basic search&replace function s/foo/bar/. Because we have hexadecimal numbers (the PCI IDs), we need to escape them with \x. \0 is a null character. More info here: [http://www.kichwa.com/quik_ref/expressions.html](http://www.kichwa.com/quik_ref/expressions.html)

It's also worth noting that the numbers are reversed, remember that the PCI ID of 88E8040T is 4355 (hex), but we write is as \x55\x43. The reason is that x86 is a little-endian architecture and the least significant bytes are written first.

---

### Post by apidej on 2008-07-01
I do following with #15 (by wanted) but after 
# modprobe sky2
my computer say :
FATAL : Could not read '/lib/modules/2.6.24-16 generic/kernel/drivers/net/sky2.ko' : invalid argument

when I type
$dmesg | grep sky2
my computer say nothing'

(My first computer TOSHIBA L310 install only Ubuntu 8.01. My computer say : No network device have been found.)
Advice me please,

---

### Post by arthurwlima on 2008-07-02
I followed the steps Wanted told, but I can't just modprobe sky2, it says it is missing a parameter (FATAL ERROR)
when I type: 
dmesg | grep sky2

I get kind of the same output, but with an extra line: 
eth0: disabling interface

Sorry I haven't print the exacts outputs, cause I'm working in a different computer now. By the way, the laptop is a Dell inspiron 1525 with Marvel 88e8040 ethernet controller. I dual boot it with Vista and the network works fine...

---

### Post by arthurwlima on 2008-07-02
Some corrections:
My chip is Marvel 88e8040, PCI_ID  0x4354, so I typed:

# perl -pe 's/\0\0\x6c\x43/\0\0\x54\x43/g' sky2.ko.orig > sky2.ko

Before modprobe, typed depmod -a. Now I've got no error messages.
But still can't get my wired network working.

After rebooting:
$ dmesg | grep sky2
[   21.776287] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   21.776751] sky2 eth0: addr 00:1d:09:54:4b:51
[   27.367482] sky2 eth0: enabling interface
[   27.921791] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   71.689160] sky2 eth0: disabling interface
[   71.719406] sky2 eth0: enabling interface
[   72.525229] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx

But can't find internet. Does someone have any idea of what's happening?

---

### Post by jeanbaptiste on 2008-07-02
> **sophie27 said:**
> Hi!
Some other friend suggest me to wait for the next Ubuntu kernel...
However It could be interesting to try with you kernel package, jeanbaptiste!
If you can do it, It would be great.(
My processor is 64 bit.)
But which are exaclty the risks in installing that? I mean, if the worst risk is that my ubuntu has to be reinstalled, it is ok; if there's the risk I all my computer, maybe it would be better to wait...


thanx so much!

Sorry I didn't check the forum for a few days. :oops:

The risk... a code which is inside the kernel can access almost all the resources of your computer. I don't want to frighten you but someone with bad intention can do a fake driver which act as a trojan.

I'm happy you (and others) have solved your problem.
Personally, to compile my kernel I downloaded the DVD version of Ubuntu. All the required packages are inside (the kernel sources also, the package is "linux-source").

The steps I used are above :
Nota : the '$' indicates the command line to type (don't type the '$' symbol...)

First install the required packages :
$sudo apt-get install libc6-dev libncurses5-dev binutils-dev linux-source

Then extract the kernel :
$cd /usr/src
$sudo tar xvjf linux-source*

Then copy the config file of the kernel into the right place :
$cd linux-source*
$sudo cp /boot/config ./.config

Modify the sky2.c file (replace [your editor] by your prefered editor, e.g. 'kate') :
$sudo [your editor] driver/net/sky2.c

Add the above line (whithout the double quotes) to the file at the line 122 (like said by pmasereeuw) :
"{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) }, /* 88E8040T */"

Then compile the whole thing :
$sudo make all && sudo make modules_install && sudo make install

Build the RAM disk (replace [kernel version] by the kernel version you're bulding e.g. 2.6.24.3) :
$sudo mkinitramfs -o /boot/initrd.gz [kernel version]

At least update your boot file (replace [your editor] by your prefered editor, e.g. 'kate') :
$sudo [your editor] /boot/grub/menu.lst

Copy-paste the first paragraph after the "## ## End Default Options ##" line (starts with 'title Ubuntu(...)') and replace on the 'kernel' and 'initrd' lines the version of the kernel by the good number (in my case it was '2.6.24-*something*' replaced by '2.6.24.3').

Then reboot and choose your new kernel at boot time.

I hope this will help.

Jean-Baptiste

---

### Post by wanted on 2008-07-02
> **arthurwlima said:**
> Some corrections:
My chip is Marvel 88e8040, PCI_ID  0x4354, so I typed:

# perl -pe 's/\0\0\x6c\x43/\0\0\x54\x43/g' sky2.ko.orig > sky2.ko

Before modprobe, typed depmod -a. Now I've got no error messages.
But still can't get my wired network working.

After rebooting:
$ dmesg | grep sky2
[   21.776287] sky2 0000:09:00.0: v1.20 addr 0xfe8fc000 irq 16 Yukon-FE+ (0xb8) rev 0
[   21.776751] sky2 eth0: addr 00:1d:09:54:4b:51
[   27.367482] sky2 eth0: enabling interface
[   27.921791] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   71.689160] sky2 eth0: disabling interface
[   71.719406] sky2 eth0: enabling interface
[   72.525229] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx

But can't find internet. Does someone have any idea of what's happening?

Well, your ethernet card is clearly available, all you need is to configure the IP settings. You can use for instance NetworkManager (the default GUI tool in Ubuntu), or manually from command line.

If you have DHCP server on the network it should be enough to just type as root:
```

# dhclient eth0
```

---

### Post by wanted on 2008-07-02
> **apidej said:**
> I do following with #15 (by wanted) but after 
# modprobe sky2
my computer say :
FATAL : Could not read '/lib/modules/2.6.24-16 generic/kernel/drivers/net/sky2.ko' : invalid argument


As someone else pointed out, try ```
depmod -a
```

---

### Post by arthurwlima on 2008-07-03
Thanks Wanted,

*dhclient eth0*  solved my trouble, 

probably it was a misconfiguration of the network

See ya

---

### Post by sergioperr on 2008-07-14
> **wanted said:**
> Yeah, rmmod was just in case you already have the module loaded in memory, but if that's not the case, then rmmod will show a harmless error message.

The "cp -p sky2.ko{,.orig}" is equivalent to "cp -p sky2.ko sky2.ko.orig", just using shell expansion for brevity. More info in "man bash", topic "Brace Expansion".

In perl I'm using the basic search&replace function s/foo/bar/. Because we have hexadecimal numbers (the PCI IDs), we need to escape them with \x. \0 is a null character. More info here: [http://www.kichwa.com/quik_ref/expressions.html](http://www.kichwa.com/quik_ref/expressions.html)

It's also worth noting that the numbers are reversed, remember that the PCI ID of 88E8040T is 4355 (hex), but we write is as \x55\x43. The reason is that x86 is a little-endian architecture and the least significant bytes are written first.

Thank you, Wanted!
It worked for me too.
I'm installing the Marvell Yukon in a Toshiba laptop M305.

---

### Post by j0se_r1v3r on 2008-07-22
> **jeanbaptiste said:**
> Sorry I didn't check the forum for a few days. :oops:

The risk... a code which is inside the kernel can access almost all the resources of your computer. I don't want to frighten you but someone with bad intention can do a fake driver which act as a trojan.

I'm happy you (and others) have solved your problem.
Personally, to compile my kernel I downloaded the DVD version of Ubuntu. All the required packages are inside (the kernel sources also, the package is "linux-source").

The steps I used are above :
Nota : the '$' indicates the command line to type (don't type the '$' symbol...)

First install the required packages :
$sudo apt-get install libc6-dev libncurses5-dev binutils-dev linux-source

Then extract the kernel :
$cd /usr/src
$sudo tar xvjf linux-source*

Then copy the config file of the kernel into the right place :
$cd linux-source*
$sudo cp /boot/config ./.config

Modify the sky2.c file (replace [your editor] by your prefered editor, e.g. 'kate') :
$sudo [your editor] driver/net/sky2.c

Add the above line (whithout the double quotes) to the file at the line 122 (like said by pmasereeuw) :
"{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4355) }, /* 88E8040T */"

Then compile the whole thing :
$sudo make all && sudo make modules_install && sudo make install

Build the RAM disk (replace [kernel version] by the kernel version you're bulding e.g. 2.6.24.3) :
$sudo mkinitramfs -o /boot/initrd.gz [kernel version]

At least update your boot file (replace [your editor] by your prefered editor, e.g. 'kate') :
$sudo [your editor] /boot/grub/menu.lst

Copy-paste the first paragraph after the "## ## End Default Options ##" line (starts with 'title Ubuntu(...)') and replace on the 'kernel' and 'initrd' lines the version of the kernel by the good number (in my case it was '2.6.24-*something*' replaced by '2.6.24.3').

Then reboot and choose your new kernel at boot time.

I hope this will help.

Jean-Baptiste

___

Modify the sky2.c file (replace [your editor] by your prefered editor, e.g. 'kate') :
$sudo [your editor] driver/net/sky2.c

$sudo [your editor] drivers/net/sky2.c

drivers

thxs

---

### Post by mgol on 2008-08-17
For people that don't want to manually patch kernel - all is done in 2.6.26 kernel:

[http://www.linuxhq.com/kernel/v2.6/26/drivers/net/sky2.c](http://www.linuxhq.com/kernel/v2.6/26/drivers/net/sky2.c)

You just need to wait for the appropriate kernel version in the repos...

---

### Post by fotis_utmost on 2008-10-13
Hi guys,

well I am really desperate... I am trying to get to work the marvell yukon 88E8040T in my new toshiba p300 laptop. I tried the above solutions, but I get the following message:

FATAL: Error inserting sky (/lib/modules/2.6.24-16-generic/kernel/drivers/net/sky2.ko): Invalid module format

Any suggestions are really appreciated! I to make this thing work!

Thanks!

---

### Post by fotis_utmost on 2008-10-14
Noone? 

I found out that kernel 2.4.26 has solved this issue. But I cannot update the kernel without an internet connection. Could anybody help me? Any other suggestions?

Thanks in advance!

---

### Post by wanted on 2008-10-29
> **fotis_utmost said:**
> 
FATAL: Error inserting sky (/lib/modules/2.6.24-16-generic/kernel/drivers/net/sky2.ko): Invalid module format


The message suggests that your module file was not patched correctly. You should restore sky2.ko from backup and try patching it once more using my procedure given earlier in the thread.

Even with the original, unpatched module you shouldn't see a message like "invalid module format" -- it should load, but just won't recognize your network card.

---

### Post by staceyhome on 2008-11-05
[I][B][I][B]> **wanted said:**
> OK, I hope the following instructions should help. All you need to do is to open a terminal and copy-paste the following commands.

```
$ sudo su -
[type your password]
# rmmod sky2
# cd /lib/modules/`uname -r`/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
# echo sky2 >> /etc/modules
# modprobe sky2

```
The last command loads the fixed driver and you should see it detect your network card like this:
$  dmesg | grep sky2
[   30.364735] sky2 0000:07:00.0: v1.20 addr 0x88000000 irq 17 Yukon-FE+ (0xb8) rev 0
[   30.365174] sky2 eth0: addr 00:1e:68:46:d3:34
[   33.962661] sky2 eth0: enabling interface

On next reboot, the driver should load automatically, so all you need to do is to configure the network parameters then.

Obviously, when you upgrade your kernel (e.g. via Synaptic) you should repeat all the commands up to the "perl" line.[/B][/I][/B][/I]

HTH.

Thanks Wanted it works brilliant, but on Kubuntu only. In Ubuntu after issuing "perl -pe ..." command I got the following error:

Unrecognised character \xC2 at -e line 1

Could You please give me a hint how to work around it? Thanks in advance!

---

### Post by bolunmez on 2008-12-26
hi i've intalled kubuntu64bit 8.10 on my toshiba a300d. i have same problem. tried to solve that using below intructions by modifying to 64bit (changed /lib/ to /lib64/). after reboot i'd tried but still have trouble. please click the link below.
[http://nopaste.ch/44b672660cbe412.html](http://nopaste.ch/44b672660cbe412.html)
U may see my work to connection after reboot. thanx
 
> **wanted said:**
> OK, I hope the following instructions should help. All you need to do is to open a terminal and copy-paste the following commands.

```
$ sudo su -
[type your password]
# rmmod sky2
# cd /lib/modules/`uname -r`/kernel/drivers/net
# cp -p sky2.ko{,.orig}
# perl -pe 's/\0\0\x6c\x43/\0\0\x55\x43/g' sky2.ko.orig > sky2.ko
# echo sky2 >> /etc/modules
# modprobe sky2

```
The last command loads the fixed driver and you should see it detect your network card like this:
$  dmesg | grep sky2
[   30.364735] sky2 0000:07:00.0: v1.20 addr 0x88000000 irq 17 Yukon-FE+ (0xb8) rev 0
[   30.365174] sky2 eth0: addr 00:1e:68:46:d3:34
[   33.962661] sky2 eth0: enabling interface

On next reboot, the driver should load automatically, so all you need to do is to configure the network parameters then.

Obviously, when you upgrade your kernel (e.g. via Synaptic) you should repeat all the commands up to the "perl" line.

HTH.



(i know, i got a poor english. :lolflag:thank u 4 your understanding)

---

### Post by staceyhome on 2009-03-30
Hi everybody,

I got it working. Somehow perl string from above gave me an error and suggestions like update of kernel libraries etc. were immediately discarded due to internet unavailability. All in all I decided to download (on another computer of course :) ) the official driver package from Marwell Yukon site and it worked for me. The only problem was install.sh script. Its first line should be changed to run this script in bash instead of Bourne shell. The other thing is to create a sym link to your current kernel source directory under /usr/src, like this:

ln -s /usr/src/kernel****generic /usr/src/linux

then run install.sh

And yes, you are right, in 8.10 (K)Ubuntu version this issue is solved by default, but Web camera doesn't work at all. As for me I prefer to spend couple of hours to find the solution for NIC instead of the fruitless research on how to enable my webcamera I have given up at the end.

---

### Post by pyrofreak99 on 2009-12-02
i am need of assistance  im running a toshiba satellite M300  and just instaled ubuntu 9.10  and so far im lost as to what to put in the terminal and such and i need my connection working 


please help

---

