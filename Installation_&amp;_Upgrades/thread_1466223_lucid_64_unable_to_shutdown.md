---
title: "lucid 64 unable to shutdown"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by tenmoi on 2010-04-30
A clean install on an all linux AMD desktop machine. Problem is lucid will not shutdown. All that you can see is the background staring at you for good.

How do I fix it?

Thanks alot.

P.S. 
I have not had the guts to install fglrx either.

Some software I did install:

sudo aptitude install subversion make g++ gcc gawk pmount libtool nasm automake cmake gperf unzip bison libsdl-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libfribidi-dev liblzo2-dev libfreetype6-dev libsqlite3-dev libogg-dev libasound-dev python-sqlite libglew-dev libcurl3 libcurl4-openssl-dev x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmad0-dev libogg-dev libvorbisenc2 libsmbclient-dev libmysqlclient-dev libpcre3-dev libdbus-1-dev libhal-dev libhal-storage-dev libjasper-dev libfontconfig-dev libbz2-dev libboost-dev libfaac-dev libenca-dev libxt-dev libxtst-dev libxmu-dev libpng-dev libjpeg-dev libpulse-dev mesa-utils libcdio-dev libsamplerate-dev libmms-dev libmpeg3-dev libfaad-dev libflac-dev libiso9660-dev libass-dev libssl-dev fp-compiler gdc libwavpack-dev libmpeg2-4-dev libmicrohttpd-dev libmodplug-dev libssh-2-dev gettext cvs
sudo aptitude install subversion make g++ gcc gawk pmount libtool nasm automake cmake gperf unzip bison libsdl-dev libsdl-image1.2-dev libsdl-gfx1.2-dev libsdl-mixer1.2-dev libfribidi-dev liblzo2-dev libfreetype6-dev libsqlite3-dev libogg-dev libasound-dev python-sqlite libglew-dev libcurl3 libcurl4-openssl-dev x11proto-xinerama-dev libxinerama-dev libxrandr-dev libxrender-dev libmad0-dev libogg-dev libvorbisenc2 libsmbclient-dev libmysqlclient-dev libpcre3-dev libdbus-1-dev libhal-dev libhal-storage-dev libjasper-dev libfontconfig-dev libbz2-dev libboost-dev libfaac-dev libenca-dev libxt-dev libxtst-dev libxmu-dev libpng-dev libjpeg-dev libpulse-dev mesa-utils libcdio-dev libsamplerate-dev libmms-dev libmpeg3-dev libfaad-dev libflac-dev libiso9660-dev libass-dev libssl-dev fp-compiler gdc libwavpack-dev libmpeg2-4-dev libmicrohttpd-dev libmodplug-dev libssh-2-dev gettext cvs subversion git
sudo apt-get install build-essential libattr1-dev libblkid-dev libgnutls-dev libreadline5-dev python-dev autoconf python-dnspython

And mysql-server, libqt4, gstream*

---

### Post by xdemo on 2010-04-30
Try open tty1 (ctrl+alt+f1) and login with your user, then in the console:
```
$ sudo poweroff
```
or
```
$ sudo halt
```

Just a temporary way to make sure your computer shuts down properly until you find out the problem.

---

### Post by tenmoi on 2010-04-30
> **xdemo said:**
> Try open tty1 (ctrl+alt+f1) and login with your user, then in the console:
```
$ sudo poweroff
```
or
```
$ sudo halt
```

Just a temporary way to make sure your computer shuts down properly until you find out the problem.

I did a shutdown -r now and still it will not shutdown. I installed fglrx downloaded from amd.com and now I cannot uninstall it. I'll try as you suggested and a reinstall is perhaps what will await me.:(

I am happy now.

I reinstalled fglrx downloaded from amd.com and restarted successfully.

Ubuntu depends on ati to shutdown:confused:

Anyway, thank you for your help.

---

### Post by cb951303 on 2010-04-30
I have a similar problem.

I did a fresh 32bit lucid install. but when I try to shutdown the computer it takes me to the login screen. then I retry shutting it down form the login screen with the shutdown button at the bottom right but it does nothing.

anyone having this problem?

---

### Post by SlugSlug on 2010-04-30
I had similar prob,

is was kexec 

cat /etc/default/kexec



# Defaults for kexec initscript
# sourced by /etc/init.d/kexec and /etc/init.d/kexec-load

# Load a kexec kernel (true/false)
LOAD_KEXEC=[COLOR=Red]false[/COLOR]

# Kernel and initrd image
KERNEL_IMAGE="/vmlinuz"
INITRD="/initrd.img"

# If empty, use current /proc/cmdline
APPEND=""

---

### Post by Ctulhu on 2010-05-01
Same problem here: shutdown from the button in the top right corner does not do anything on a newly installed 10.4 32bit system, but

sudo shutdown now

at the terminal works. Somewhat annoying ...

---

### Post by cb951303 on 2010-05-02
> **Ctulhu said:**
> Same problem here: shutdown from the button in the top right corner does not do anything on a newly installed 10.4 32bit system, but

sudo shutdown now

at the terminal works. Somewhat annoying ...

it was somehow fixed when I restarted the computer.

---

### Post by theoldgit on 2010-05-03
I am having this problem at what appears to be random times. ie sometimes it works perfectly well, other times I'm back to the login screen and an endless loop.

---

### Post by Ctulhu on 2010-05-03
Yea, sometimes it works, sometimes it doesn't. Sometimes also

sudo shutdown now

hangs at the aubergine shutdown screen. Can we just shutdown our OSs plz??

---

### Post by Jenske on 2010-05-06
In my case (and having read it somewhere else on the internet) it has something to do with the OpenOffice Quickstarter. If I shut this down AND AFTERWARDS shut down Ubuntu 10.04, no problem: the system shuts down.

If, however, I keep the Quickstarter, shutdown, then nothing happens (i.e. I see the background image and can continue working in Ubuntu as if nothing ever happened).

---

### Post by alh on 2010-05-06
Same with me and openoffice qickstarter. Don't use it and now don't have a problem. Stopped it in openoffice pref or stop in start apps. Bit of a glitch there?
 
Dosen't make that much differece in programme startup time anyway.

---

### Post by fromgi on 2010-05-07
Never activated Quickstarter and still have the problem.

---

### Post by Ctulhu on 2010-05-14
disabling the OpenOffice systray quickstarter did it for me

---

### Post by AGAUT on 2010-05-14
Hi,
 
I am having same problem; though it started occuring after I removed the 'power' button and then added again in the panel. Earlier it was working fine but now i have to shut down computer directly from the CPU :(
 
Will try by the command line but is there a permanent solution??

---

### Post by SilFox on 2010-07-24
My Lucid x64 worked OK _until I changed graphic card_ (downgraded from [nVidia 280]("http://www.bfgtech.com/bfgrgtx2801024oce.aspx") to[ nVidia 8500]("http://www.pcstats.com/articleview.cfm?articleID=2184") ). After that I am unable to shutdown (*restart* works OK). Also, it happens with OR without proprietary drivers. (I didn't try drivers downloaded manually from nvidia, only those ofered by Ubuntu).

Today, on same desktop computer, I tried Ubuntu 10.10 [64bit] Alpha2 (2.6.35) and OpenSuse 11.3 [64bit] (2.6.34);
Ubuntu 10.10 goes black screen few seconds after I press "Try Ubuntu without install..." ;
OpenSuse 11.3 after finishing installation, on first reboot (when installation goest to final stage) - also went black screen. And, I couldn't go to console or do anything else.
Seems that newer kernels don't like my graphic card (?)

```

sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G86 [GeForce 8500 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:18 memory:fd000000-fdffffff  memory:d0000000-dfffffff(prefetchable) memory:fa000000-fbffffff  ioport:d800(size=128) memory:feae0000-feafffff(prefetchable)

```Also, I tried Ubuntu 10.10 Alpha2 [64bit] on Laptop Acer Aspire 7730G and it worked OK.

Managed to boot Live CD Ubuntu 10.10 Alpha2 x64 on desktop computer;
on first screen, before I press "Try Ubuntu ...", I pressed F6 and picked "nomodeset"

Still no luck in finding solution how to poweroff my installed Lucid on that desktop computer.

---

### Post by BertjeBebo on 2010-08-12
> **AGAUT said:**
> Hi,
 
I am having same problem; though it started occuring after I removed the 'power' button and then added again in the panel. Earlier it was working fine but now i have to shut down computer directly from the CPU :(
 
Will try by the command line but is there a permanent solution??

Same problem, same solution ;)

I hope it is permanent.

---

### Post by SilFox on 2010-08-28
Today I switched back previous graphic card and reinstalled Lucid; and, guess what, 'Poweroff' problem IS still here, so maybe in this case, that bug is not related to graphic card.

However, noticed that there is new release of [Ubuntu 10.10 (Maverick Meerkat) ALPHA **3**]("http://www.ubuntu.com/testing/maverick/alpha3") , so I decided to try it, and - **it shutdown normally**.

After updating, [there is one (solvable) bug - related to shutdown/restart]("https://bugs.launchpad.net/ubuntu/+source/policykit-1-gnome/+bug/623819"); (it is still alpha!)
> _In a fully updated maverick_amd64_ the newest policykit-1-gnome_0.96-2ubuntu**3**
does not let me reboot nor shutdown. This is a recent update.
 After I have pressed the reboot or shutdown button from the user menu, a small window opens with an error text:
"**policykit is not responding**".
If I then press the button "shutdown anyway", **the computer reboots or shuts down within 10 seconds, but not immediately.**
 This has something to do with user rights, because if I command in terminal:
sudo reboot or
sudo halt (sudo poweroff)
the combuter responds immediately without any errors.
 Also,[B] if I downgrade the policykit-1-gnome and libpolkit-gtk-1-0 packages to the version 0.96-2ubuntu2, the issue is gone
and the user menu works as it should.[/B]
So, I found and manually downloaded "policykit-1-gnome_0.96-2ubuntu**2**_amd64.deb" and "libpolkit-gtk-1-0_0.96-2ubuntu**2**_amd64.deb", and installed them:
```
fox@MSI:~/Downloads$ sudo dpkg --force-depends -i policykit-1-gnome_0.96-2ubuntu2_amd64.deb
fox@MSI:~/Downloads$ sudo dpkg --force-depends -i libpolkit-gtk-1-0_0.96-2ubuntu2_amd64.deb
```Then restarted computer, and just as Harry said, "the issue is gone and the user menu works as it should."

---

### Post by SilFox on 2010-09-03
New Maverick update for PolicyKit~ :
> Changes for the versions:  
 0.96-2ubuntu2  
 0.96-2ubuntu[COLOR=DarkRed]4[/COLOR]  
 
 Version 0.96-2ubuntu4:  
 
   * debian/patches/04-autorestart.patch:  
     - updated to implement the full gnome-session API to prevent  
       "authentication agent is not responding" message on logout  
 I installed this update and shutdown issue is gone;
BTW, Ubuntu 10.10 [COLOR=DarkRed]beta[/COLOR] version is available on ubuntu.com

---

