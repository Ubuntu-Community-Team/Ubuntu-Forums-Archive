---
title: "Need help installing from a tar.gz"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by testbenchdude on 2008-10-07
Hello all,

I am sorry to have to ask such a newbie question but I am flummoxed. I have a fresh install of Hardy on my new Dell Studio but unfortunately it installed without the wireless drivers (a problem that I read will be remedied in the 8.10 release). No big deal, right? I found a link to the driver on Dell's blog page but the page won't load. So I googled around a bit and found a driver from Broadcom.

Here's my problem. I unzipped the file I downloaded into a new folder. The files are lib, src, and Makefile. I do not know what to do with these files! I've successfully installed build-essential via apt-get, but ./configure doesn't do aything, nor do the make or make install commands. I have been trying now for about an hour to find out how to install this driver with no luck. I am completely lost as to what to do with these files! 

So very frustrating!

Thanks for any advice anyone can give.

---

### Post by tuxxy on 2008-10-07
make sure you are working in the correct directory first, so if located on your desktop type,

```
cd Desktop
```

Then configure it

```
./configure

```

If you receive no errors then run

```
make
```

and finally

```
sudo make install
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by testbenchdude on 2008-10-07
Hi tuxxy,

I created a folder called wireless on my desktop and that's where I unzipped the files to. I navigated to that folder in terminal, and when I type ```
ls
``` I get three files: lib, src, and Makefile. So I know I'm in the right folder. Then I type ```
./configure
``` and I get this:

```
bash: ./configure: No such file or directory
```

What am I doing wrong? I also tried ```
sudo ./configure
``` and got the same result.

Thanks for trying to help.

---

### Post by iponeverything on 2008-10-07
post the link to the driver you downloaded and I'll take a look at it.

---

### Post by testbenchdude on 2008-10-07
I found it here:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I downloaded the 64 bit version (64 bit version of Hardy is installed).

Thanks

---

### Post by iponeverything on 2008-10-07
When you downloaded the driver you may have overlooked the 

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

It has some good instructions on building the driver.

Take a look, go as far as you can with them and post back if you run into problems.

It's bedtime here, so I may check back in about 10 hours or so..

---

### Post by testbenchdude on 2008-10-07
You're right, I completely missed that! Good catch.  However...

I get up to step number 4 and again I'm stumped. I'm guessing I need to replace the 2.6.xx.xx with my kernel version number, right? So after googling on how to find that, I did this:

```
uname -a

```
Result:

2.6.24-19-generic #1 SMP Wed Aug 20 17:53:40 UTC 2008 x86_64 GNU/Linux

Here are the instructions:
> 
1.  Create a new directory:                 mkdir hybrid_wl
2.  Go to that directory:                   cd hybrid_wl
3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                             tar -xzf <path>/hybrid-portsrc.tar.gz
        64 bit:                             tar -xzf <path>/hybrid-portsrc-x86_64.tar.gz

After untar'ing you should have a src and lib sub directory plus a Linux
2.6 "kbuild" external makefile (Makefile).   The lib sub directory has the pre-built
binary, wlc_hybrid.o_shipped.  

You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable
kernel module (LKM):

On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`

I can't figure out the correct thing to put in place of the xx's. Why is this such a mystery? I'm getting frustrated more and more with this, thanks again for everyone's help.

---

### Post by phidia on 2008-10-07
First the terminal (bash) has command line completion so whenever you are unsure of the full path name just type part of the string and press the tab key.

What do you have in lib/modules? Just cd there and enter "ls".

---

### Post by issih on 2008-10-07
Try 2.6.24.19 as shown by the output of the uname command you posted.

Unfortunately when the manufacturers don't provide drivers for their hardware things can be awkward to get working. Broadcom only very recently released drivers, so they have not worked their way into the repositories yet.

No point getting frustrated by it, nobody wants it to be difficult, its just unfortunate. Keep plugging away and it'll work eventually, plus you'll have learnt lots :)

Try to think of it that way.

Hope that helps

---

### Post by onero on 2008-10-07
/lib/modules/<2.6.xx.xx>/build is just the path; if you want to be sure, in Nautilus you can navigate to /lib/modules and look for your kernel folder there.

Most likely though, you just need to replace <2.6.xx.xx> with 2.6.24-19-generic (so /lib/modules/2.6.24-19-generic/build).

---

### Post by testbenchdude on 2008-10-07
> **phidia said:**
> First the terminal (bash) has command line completion so whenever you are unsure of the full path name just type part of the string and press the tab key.

What do you have in lib/modules? Just cd there and enter "ls".

How do I use this "command line completion"? I don't understand what you are asking. I think I know the full path name, isn't it /lib/modules? The only two files in there are 2.6.24-16-generic and 2.6.24-19-generic. When I type this:

```
make -C /lib/modules/<2.6.24-19-generic>/build M='pwd' clean
```

I get this:
> 
bash: 2.6.24-19-generic: No such file or directory

I'll keep plugging away I guess, but this is borderline ridiculous. I have worked over two hours on this now.

---

### Post by testbenchdude on 2008-10-07
> **onero said:**
> /lib/modules/<2.6.xx.xx>/build is just the path; if you want to be sure, in Nautilus you can navigate to /lib/modules and look for your kernel folder there.

Most likely though, you just need to replace <2.6.xx.xx> with 2.6.24-19-generic (so /lib/modules/2.6.24-19-generic/build).

Now I just feel dumb. How was I supposed to know that these symbols <> were extraneous? Meh.

Moving on, here is what I typed:
```

 make -C /lib/modules/2.6.24-19-generic/build M=`pwd` clean
```

Here is the result (after I realized I needed to do this from the folder I created):

> 
make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

Then step 5:

```

 make -C /lib/modules/2.6.24-19-generic/build M=`pwd`

```

delivers this:

> 
make: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  LD      /home/mikeyc/Desktop/Wireless/hybrid_wl/built-in.o
  CC [M]  /home/mikeyc/Desktop/Wireless/hybrid_wl/src/wl/sys/wl_linux.o
  CC [M]  /home/mikeyc/Desktop/Wireless/hybrid_wl/src/wl/sys/wl_iw.o
  CC [M]  /home/mikeyc/Desktop/Wireless/hybrid_wl/src/shared/linux_osl.o
  LD [M]  /home/mikeyc/Desktop/Wireless/hybrid_wl/wl.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mikeyc/Desktop/Wireless/hybrid_wl/wl.mod.o
  LD [M]  /home/mikeyc/Desktop/Wireless/hybrid_wl/wl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

Success! I think. Now what? The README says to do this:

> On this or a machine with the same kernel version, install the driver.

1.  Validate you don't have loaded (or built into the kernel) the Linux community provided
      driver for Broadcom hardware.  This exists in two forms: either "bcm43xx" or a split form
      of "b43" plus "b43legacy".  If these modules were loaded you would either
        a) rmmod bcm43xx or
        b) rmmod b43; rmmod b43legacy
2.  Make available 802.11 TKIP crypto module:      modprobe ieee80211_crypt_tkip
3.  Insert the Broadcom wl module:                 insmod <path>/wl.ko

I don't appear to have any other Broadcom drivers as far as I can see, so the first instruction returned

> ERROR: Module b43legacy does not exist in /proc/modules

Then I typed this:

```
modprobe ieee80211_crypt_tkip
```

and got this:

> WARNING: Error inserting ieee80211_crypt (/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt.ko): Operation not permitted
FATAL: Error inserting ieee80211_crypt_tkip (/lib/modules/2.6.24-19-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko): Operation not permitted

I think I'm missing a permission somewhere or something...

---

### Post by issih on 2008-10-07
leave out the < and >, you need to specify the directory exactly.

i.e. you need to use the full path to the directory:

```
/lib/modules/2.6.24-19-generic
```

Or whatever the exact path is on your system.

Command line completion simply refers to the fact that when you have typed a partial command/path in the terminal, if you then hit tab the terminal will try and complete the command from the available options. If there is more than one option so it can't be completed then hitting tab twice will present a list of the possible options.

In this case, if you typed "/lib/modules/2.6" then hit tab it should complete that to "/lib/modules/2.6.24-1" as both possible commands have that starting substring, adding the 9 and hitting tab again will complete the whole path.

Hope that helps

---

### Post by issih on 2008-10-07
You need to use sudo in front of the modprobe commands to gain root privileges. just type it as :

```
sudo modprobe <name of module>
```

and enter your login password when prompted.

---

### Post by testbenchdude on 2008-10-07
Got it, thanks. I was able to complete the procedures by logging in as root. I also followed part of another guide here:

[http://www.uluga.ubuntuforums.org/showthread.php?t=896713](http://www.uluga.ubuntuforums.org/showthread.php?t=896713)

and I did not get any error messages, so hopefully everything works. I'm going to test it out and report back. Thanks everyone for the help and insight.

Cheers~

---

### Post by testbenchdude on 2008-10-07
Success indeed! I'm now on my wireless network! Whew. Thanks again, all.

---

### Post by issih on 2008-10-07
Excellent, glad you got it sorted..

---

### Post by n00bz on 2009-09-13
as my name suggests, i am the biggest noob of them all, and i have the same problem, only i'm using the 32-bit. i login to as root. i read that you ran into problems with this so i thought, lets start off as the 'Super User' to reduce the problems, but i cant seem to get past step 3. it seems that what ever i type the outcome is always the same

3.  Untar the appropriate 32/64 bit file
      to that directory
        32 bit:                                                  tar -xzf <path>/hybrid-portsrc-x86_32-v5_10_91_9.tar.gz

this is what i type 

root@mobius:/home/john/wdriver#   tar -xzf home/hybrid-portsrc-x86_32-v5_10_91_9.tar.gz

and i get

tar: home/hybrid-portsrc-x86_32-v5_10_91_9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


any help is greatly appreciated

---

