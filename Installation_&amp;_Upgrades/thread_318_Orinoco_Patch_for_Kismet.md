---
title: "Orinoco Patch for Kismet"
date: 2004-10-12
forum: Installation &amp; Upgrades
---

### Post by react on 2004-10-12
I've been trying to setup Kismet on Ubuntu w. an Orinoco Gold Classic card and i have reached the point where i am supposed to patch my driver - but im not too sure what would be the best way to go about this? I know i have to grab a [patch or driver] from [http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html) but am lost after that... :-s

```
mobilemonkey&#58;/sbin# kismet
Server options&#58;  none
Client options&#58;  none
Starting server...
Will drop privs to react &#40;1000&#41; gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 &#40;orinocosource&#41;&#58; Enabling monitor mode for orinoco source interface eth1 channel 6...
Waiting for server to start before startuing UI...
FATAL&#58; Could not find 'monitor' private ioctl or use the newer style 'mode monitor' command.  This typically means that the drivers have not been patched or the correct drivers are being loaded. See the troubleshooting section of the README for more information.

```

```
mobilemonkey&#58;/sbin# dmesg | grep orinoco
orinoco.c 0.13e &#40;David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others&#41;
orinoco_cs.c 0.13e &#40;David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others&#41;
```

---

### Post by disposable on 2004-10-13
If I'm correct, the latest kernel supported by the 13e patch is 2.6.2. Maybe try CVS? Also, try the forums at kismetwireless.net.

---

### Post by stonersavant on 2004-12-25
Argh... I go to the kismet forums, they tell us to go to the ubuntu forums...

I come to the Ubuntu forums, they tell us to go to the Kismet forums.

Has anyone gotten the orinoco drivers patched under Ubuntu? I used orinoco-0.15rc2 and kismet SEEMS to like it, but when I type  /sbin/iwpriv it does NOT list monitor mode. Any idea why kismet seems to like the drivers ok, but airsnort doesn't?

---

### Post by macpilot on 2004-12-30
Any luck with the howto patch the orinoco driver, I'm also stuck there

---

### Post by macpilot on 2005-01-04
[QUOTE=macpilot]Any luck with the howto patch the orinoco driver, I'm also stuck there[/QUOTE]
 Ok, I was able to patch the files however when I try tu compile the modules
make modules SUBDIRS=drivers/net/wireless

I get the error:
Makefile:418: .config: No such file or directory
  Building modules, stage 2.
/usr/src/linux-source-2.6.8.1/scripts/Makefile.modpost:38: .config: No such file or directory
make[1]: *** No rule to make target `.config'.  Stop.
make: *** [modules] Error 2

How do I get past this? I'm fairly new to linux so I'm lost

---

### Post by smithe on 2005-01-04
Unfortunately, I just received my Orinoco Gold Classic (Proxim) 8410-WD in the mail a few days ago, and I must also get on the "how do I patch for monitor mode".  If ANYONE has done this successfully, please help us here in the forum.  

I've tried 2 kernels, three variations of firmware, and a whole slew of pcmcia versions...I'm at a loss.  I think it is a variety of things working in tandem to defeat me.

I think the new kernel isn't working with the newest orinoco drivers which are supposed to support monitor mode unpatched, but may not.  Or something.  

Back to the Google machine.....

 :confused:

---

### Post by jdodson on 2005-01-05
if you still have no luck with the driver i have and successfully configured with no problems, ndiswrapper.  ndiswrapper takes the windows driver and makes it usable in gnu/linux.

you can do a forum search for a better howto on it, needless to say i did not find in really tough to setup by compiling it from source as the docs that come with the package are well written.

---

### Post by Ciaran m on 2005-02-01
I've been trying to get my Truemobile 1150 wireless card to work with Kismet but i'm not too sure how to do it. Hopefully someone can point me in the right direction.

I understand the card is the same as an orinoco but with a truemobile sticker on it, please correct me if i'm wrong. At the moment i'm using the card to connect to an ap upstairs and it works fine.
So now i want to go and find some new signals and check existing ones. I have just swithed completely from xp to ubuntu and was using netstumbler with xp.

I have installed kismet "sudo apt-get install kismet"
when i start kismet it sayes something about no driver.
I have downloaded the laterst driver to my desktop but i don't know what to do with it from there.
Sorry to seem so stupid but can someone give me some direction please? 8-[

---

### Post by Ciaran m on 2005-02-02
can someone help me please  :cry:

---

### Post by Technoviking on 2005-02-03
The orinoco driver from the orinoco CVS will compile under Ubuntu. It has monitor mode built in (iwconfig ethx mode monitor to activate).

Mike

---

### Post by Ciaran m on 2005-02-04
pardon my ignorance, what does CVS mean, where is this driver
Thanks

---

### Post by Technoviking on 2005-02-04
[QUOTE=Ciaran m]pardon my ignorance, what does CVS mean, where is this driver
Thanks[/QUOTE]
CVS is the Concurrent Versions System, the dominant open-source network-transparent version control system. It basically downloads the current code base that the developers are working on.
CVS Info: [https://www.cvshome.org/](https://www.cvshome.org/)

To install CVS on Ubuntu 
```

sudo apt-get update
sudo apt-get install cvs

```

Orinoco CVS page: [http://savannah.nongnu.org/cvs/?group=orinoco](http://savannah.nongnu.org/cvs/?group=orinoco)

Mike

---

### Post by Ciaran m on 2005-02-04
I looked at that and it all seems very complicated but i'm sure it's not. the  cvs manual is about 200 pages.
i did this:
export CVS_RSH="ssh"

cvs -z3 -d:ext:anoncvs@savannah.gnu.org:/cvsroot/orinoco co orinoco

and it did a load of stuff, then i tried

iwconfig eth1 mode monitor

but i just got this :
root@laptop-home:/home/ciaran # iwconfig eth1 mode monitor
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.
 
Can you furthur my progress please, your help has been great so far
Ciaran 8-)

---

### Post by ubernoob on 2005-02-23
I have the same problem! I followed this guide:

[http://www.ubuntulinux.org/wiki/InstallingCompaqW200](http://www.ubuntulinux.org/wiki/InstallingCompaqW200)

so i was sure i had the newest orinoco driver installed. But I'm not able to set it in monitor mode either! Does anyone know how to fix this?

---

### Post by wernst on 2005-03-10
[QUOTE=ubernoob]I have the same problem! I followed this guide:

[http://www.ubuntulinux.org/wiki/InstallingCompaqW200](http://www.ubuntulinux.org/wiki/InstallingCompaqW200)

so i was sure i had the newest orinoco driver installed. But I'm not able to set it in monitor mode either! Does anyone know how to fix this?[/QUOTE]

Well...

Though I didn't plan on doing this, below you'll find ALL the instructions you need to download, compile, and install the latest CVS Orinoco drivers (which have built-in monitor mode) on Ubuntu 4.10 (Warty Warthog). Then I'll show you how to  download, compile, install, and use (at least basically) Airsnort.

I wrote this while I did it. I Ghosted back a few times to make sure it works and to follow what were ultimately dead ends to their conclusion. 

I hope you (and anyone who reads this in the archives) finds it useful:

-Warr

------------------snip-----------------

Here are some steps to get Airsnort working on Ubuntu.

- Back up your system. I like using Norton Ghost 2003. It is much easier thrashing around the system trying things when you know you can go back to a working setup. Think of it as a system-wide Undo.

- Find out what kernel you are running. You can open a terminal window and type "uname -r", or you can look at the GRUB bootloader screen. Write down what it says. In my case it is "2.6.1-4-686".

- Download the latest CVS version of the Orinico driver. I found it at:
[http://savannah.nongnu.org/cgi-bin/viewcvs/*checkout*/orinoco/orinoco/index.html?rev=1.22&cvsroot=Web](http://savannah.nongnu.org/cgi-bin/viewcvs/*checkout*/orinoco/orinoco/index.html?rev=1.22&cvsroot=Web)

after going to:
[http://savannah.nongnu.org/cvs/?group=orinoco](http://savannah.nongnu.org/cvs/?group=orinoco)

The result will be a tarbar. The file I got was: orinoco-0.15rc2.tar.gz

- OK, we need to uncompress it and work with it. If you're a GUI person, double-click the download, which opens it in File Roller, which is Gnome's archive manager. (Think Winzip.) Click the Extract button, make a new folder in your Home directory by clicking "Create Folder" and naming it something like "orinoco_cvs_driver", then click "Extract". Close File Roller. If you're not a GUI person, then you almost certainly know how to deal with a tarball on the command line.

- This makes a folder in your Home folder called "orinoco_cvs_driver" and inside this is a folder called "orinoco-0.15rc2" (at least for me. Version numbers can change.)  Inside "orinoco-0.15rc2" are all the files we need to compile and work with.

- Since we need to compile things, you need a few tools and files in order to compile. Open Synaptic Package Manager (Computer menu > System Configuration > Synaptic Package Manager) and use the Search function to find "linux-headers-(version #)" and highlight those items. In my case it was "linux-headers-2.6.8.1-4-686" and  "linux-headers-2.6.8.1-4". Then click "Apply" and then "Apply" again to get them. Use the same procedure to get "build-essential" (which also gets a lot of depandant things).

- A lot of people will tell you that you should move this folder of stuff to a "proper" working directory, like /usr/src or usr/local/src, and if you want to, go ahead. I don't bother with this. You also need to do a lot of things as root, which in Ubuntu is different. I just open up a Root Terminal window (Applications menu > System Tools > Root Terminal) but you can run "sudo" all the time in a regular terminal window if you like. These instructions assume you'll use the Root Terminal.

- Go to the folder with all the orinoco files. There's a "README.orinoco" file in there. I'd read it for any last minute instructions.

- Open your Root Terminal window and move to the orinoco folder with all the files. In my case, that is: /home/wernst/orinoco_cvs_driver/orinoco-0.15rc2.

- Type "make" (no quotes). After a moment, you should get a prompt again, and without errors.

- Type "make install" (no quotes). If you aren't doing this in a root terminal, then the command is "sudo make install" (no quotes) and enter your password. This installs the driver to the correct location. 

- (Note - if and when you upgrade your kernel or Ubuntu in general, if the new features of these Orinoco drivers stop working, it is because the update overwrote these files you just built. If that's the case, download the new Linux headers that correspond to whatever new kernel you have, and then do a "make" and "make install" with these files again, and you should be good to go.)

- Restart the computer. Make sure wireless access still works. If it does: good! You didn't break anything.

- You're probably doing all this to get the monitor modes working for Airsnort and other similar tools. To manually start monitor mode, first "disable" the wireless interface (eth1, in my case) in the Gnome networking panel (Computer menu > System Configuration > Networking).  Theres also a command line, um, command you can do as root, but I forget what that is. (I *think* its "ifconfig eth1 status down" but don't hold me to that.)

- Open a Root Terminal window. Type the command: "iwconfig eth1 mode monitor" (no quotes). You should see no error message. If you re-enable the wireless card in the Networking panel and try to ping other things, it shouldn't be able to. That's because you're in Monitor mode! Congratulations!

- Restart the system to get your normal wireless connection working again. To use an older version of Airsnort (0.23d), just select it from Synaptics. Then open a Root Terminal window. Start monitor mode (iwconfig eth1 mode monitor). Start Airsnort by typing "airsnort" (no quotes). Click "Refresh" once. Set Network Device to whatever your wireless card is (eth1 for me). Set Driver Type to "Host AP/Orinoco". Then click "Start" to start. Your capturing! Restart computer to reset interface (ejecting and inserting PCMCIA card should do it too).

- If you're looking for the latest Airsnort, download the latest package from [http://airsnort.shmoo.com/](http://airsnort.shmoo.com/). As of now, the latest version is 0.27e, so the download file is: airsnort-0.2.7e.tar.gz. As before, double-click it to open it in File Roller. Uncompress it someplace safe; I made an "airsnort" folder in my Home folder and uncompressed it there, which made a folder called "airsnort-0.2.7e" within "airnsort".  There's a README file you should check for any last minute instructions, along with an INSTALL file.

-Building airsnort requires some more things, but they are installable via Synaptic. I THINK all you need to install is "libgtk2.0-dev" but I also installed "libgtk1.2-dev" to be safe. You also need "libpcap0.8-dev."

- Open a Root Terminal window and move into the airsnort directory with all the files. For me, that's: /home/wernst/airsnort/airsnort-0.2.7e. Start with typing "./configure" (no quotes). This makes sure you've got the right building blocks to build. If there are no errors...

- Then do a "make" and "make install" (no quotes). With any luck, this puts an airsnort executable in /usr/loca/bin, which happens to be in the PATH.

- To run it, open a Root Terminal window and type "airsnort" (no quotes). The latest version of Airsnort AUTOMATICALLY ENABLES MONITOR MODE. You don't even need to disable the wireless interface (like eth1) first. Just make sure "eth1" and "Host AP/Orinoco" are selected in Airsnort and click "Start." To stop, click "Stop." You won't be able to go online while scanning, but the connection will be restored to normal when you stop scanning.

- Interested in the latest versions Ethereal and Kismet? You're in luck! They use the updated CVS-based Orinoco drivers too. I am not going to go through the steps, but if you paid attention to how to make Airsnort, then you'll do fine. The basic deal is to download the source tarball, uncompress it, read any README or INSTALL files that came with the package. Use Synaptics to download any required dependancies. You'll be told to "./configure", "make", and "make install". You may (will) get errors during your ./configures and makes, BUT stay calm and read them. If, for example, the error message says "yaff not found" then use Synaptics to search for "yaff" and install it, and then try the ./configure or make again. Doing nothing more than this, Ethereal and Kismet will compile, install, and work.

- Don't mind using older versions of Kismet and Ethereal? Just use Synaptics to get them.

Want to know how to actually *use* these programs? I'm the wrong person to ask.

- Warren Ernst

---

### Post by gerv on 2005-10-15
For Breezy with orinoco-1.5rc3, I've found you have to do at least two additional things:

1) Install gcc-3.4, which is not the default compiler but it's the one used for the kernel
2) Hack the Orinoco Makefile so it can find the linux kernel headers. The first line sets the path; whatever magic command it uses doesn't work. Set the value manually to /usr/src/linux-headers-blah, where the directory name "blah" includes the architecture (e.g. 686).

However, having done both of those and having got a successful compile, "make install" seems to work but after a reboot, I still can't get monitor mode working. I just get an error, as if the drivers weren't being used. Anyone got any ideas?

---

### Post by jshein on 2005-10-19
A step by step breezy version of my howto can be found here 

HOWTO: 5.10 ( Breezy ) + Orinoco CVS + Monitor Mode + Kismet
[http://ubuntuforums.org/showthread.php?p=427388#post427388](http://ubuntuforums.org/showthread.php?p=427388#post427388)

---

### Post by NetPyro on 2005-12-18
[QUOTE=react]I've been trying to setup Kismet on Ubuntu w. an Orinoco Gold Classic card and i have reached the point where i am supposed to patch my driver - but im not too sure what would be the best way to go about this? I know i have to grab a [patch or driver] from [http://airsnort.shmoo.com/orinocoinfo.html](http://airsnort.shmoo.com/orinocoinfo.html) but am lost after that... :-s

```
mobilemonkey:/sbin# kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to react (1000) gid 1000
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (orinocosource): Enabling monitor mode for orinoco source interface eth1 channel 6...
Waiting for server to start before startuing UI...
FATAL: Could not find 'monitor' private ioctl or use the newer style 'mode monitor' command.  This typically means that the drivers have not been patched or the correct drivers are being loaded. See the troubleshooting section of the README for more information.

```

```
mobilemonkey:/sbin# dmesg | grep orinoco
orinoco.c 0.13e (David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others)
orinoco_cs.c 0.13e (David Gibson &lt;hermes@gibson.dropbear.id.au&gt; and others)
```[/QUOTE]
Ok to answer the original question: Yes it can be done.  In fact, I just finished what you're trying to do, myself, 5 minutes ago.  I have the exact same wireless card.  I'm running Slackware right now, but I know the ubuntu-specific stuff.  The general steps we are going to take is get the pcmcia-cs-3.2.8 source (A service that manages pcmcia cards//however, if you already have your pcmcia-cs source installed from the ubuntu cd, that will work fine too.  The version that comes initially with ubuntu is like 3.2.5 I think, just substitute that information later on in the tutorial),  then we are going to download and patch the orinoco driver.  Then we're going to install the patched drivers.  Here goes nothing!

Part One:

1.  Download the pcmcia-cs-3.2.8 source and untar it.
[http://prdownloads.sourceforge.net/pcmcia-cs/pcmcia-cs-3.2.8.tar.gz?download]("http://prdownloads.sourceforge.net/pcmcia-cs/pcmcia-cs-3.2.8.tar.gz?download")

2.  Download the orinco .013e driver from:
            [http://ozlabs.org/people/dgibson/dldwd/orinoco-0.13e.tar.gz]("http://ozlabs.org/people/dgibson/dldwd/orinoco-0.13e.tar.gz")
    and untar it.

3.  Download the Orinoco .013e dragorn patch, also referred to as the "rfmon-dragorn"         patch from and copy it into the folder you untar&#8217;d the driver to.       

[http://www.kismetwireless.net/code/orinoco-0.13e-rfmon-dragorn3.diff]("http://www.kismetwireless.net/code/orinoco-0.13e-rfmon-dragorn3.diff")

Now that we have everything downloaded, and untar&#8217;d, we need to patch and then install.

Part Two:

1.  Cd into the directory you untar&#8217;d the source to. Type &#8216;make config&#8217;  After you type that it will prompt you for lots of information, just hit enter to every question without typing anything else (thus selecting the safe, default answer). Next type &#8216;make all&#8217; Hopefully this all works for you, it did for me.

2.  Here is where our process differs.  My slackware distro already had pcmcia-cs-3.2.8 installed.  Now, after successfully building the source, you are going to install pcmcia-cs-3.2.8 by typing &#8216;make install&#8217;  Hope that worked! Because I don&#8217;t have any background in troubleshooting that package installation otherwise.

3.  Assuming that all installed well, the next step is to patch the Orinoco drivers.  CD into your Orinoco directory. And execute the command: &#8220;patch &#8211;p1 < Orinoco-0.13e-rfmon-dragorn3.diff&#8221;  After that is done, we need to modify the &#8220;Makefile&#8221; file, to point correctly to your newly compiled pcmcia-cs sources.  Open up Makefile with your favorite editor, and edit the line &#8220;PCMCIA_CS = &#8220; so that it points to the absolute path of your pcmcia-cs source.  Save the file and exit your editor.

4.  Now that your Orinoco drivers are patched, type &#8220;make&#8221; Once that is done, type &#8220;make install&#8221; And that should be it!  Enjoy kismet!  Write me if you have any questions, and all the web-sites I referred to for information will follow:

[ http://www.kismetwireless.net/download.shtml#orinoco](&#8221;http://www.kismetwireless.net/download.shtml#orinoco&#8221;)

[ http://www.nongnu.org/orinoco/documentation/ ]("http://www.nongnu.org/orinoco/documentation/&#8221;)

[ http://airsnort.shmoo.com/orinocoinfo.html ]("http://airsnort.shmoo.com/orinocoinfo.html&#8221;)

Best of luck!

---

### Post by masha9966 on 2007-05-15
> **stonersavant said:**
> Argh... I go to the kismet forums, they tell us to go to the ubuntu forums...

I come to the Ubuntu forums, they tell us to go to the Kismet forums.

Has anyone gotten the orinoco drivers patched under Ubuntu? I used orinoco-0.15rc2 and kismet SEEMS to like it, but when I type  /sbin/iwpriv it does NOT list monitor mode. Any idea why kismet seems to like the drivers ok, but airsnort doesn't?


[bread mapquest bread pollution Equity Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

