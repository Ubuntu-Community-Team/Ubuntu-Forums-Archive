---
title: "How to install synaptic on an offline ubuntu computer?"
date: 2015-03-14
forum: Installation &amp; Upgrades
---

### Post by newbie14 on 2015-03-14
While I am currently connected to the internet using windows computer;
What website page should I visit to download the synaptic installer file?
What file / files should I download from the internet?
What file / files should I copy to my second USB flash disk?
At which directory should I paste the synaptic installer file to at my ubuntu computer at home?

Some background story:
My ubuntu computer's specification:
My Ubuntu computer is located at my home.
My Ubuntu computer does not have any internet connection.
It is absolutely impossible to connect my ubuntu computer to the internet.
My Ubuntu computer only has 2 (two) working USB slot.
USB slot 1 is connected to a 32 gigabyte USB flashdisk from which the ubuntu is booted from.
USB slot 2 is the only way for my ubuntu computer to obtain any installation files from my second USB flash disk.
My second USB flash-disk's capacity is 16 gigabyte.
My only access to internet is at the internet computer rental at the next city from my home.
all computers in the internet computer rental use windows operating system.
The distance from my home to the internet computer rental is 10 kilometers.
The distance from the internet computer rental to my home is 11.5 kilometers.
I have never seen any program installation process on an offline linux or ubuntu computer before in my life.
I need direct, step by step technical instructions.
I only respond to technical instructions.
Posting my every progress in a very exact, detailed and tediously is my hobby.

[B]SOLUTION:
[/B]
Step 1: Go to [http://mirrors.kernel.org/ubuntu/pool/universe/s/synaptic/synaptic_0.81.1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/s/synaptic/synaptic_0.81.1_i386.deb)
Step 2: Download the synaptic_0.81.1_i386.deb file
Step 3: Go to [http://mirrors.kernel.org/ubuntu/pool/main/libe/libept/libept1.4.12_1.0.12_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/libe/libept/libept1.4.12_1.0.12_i386.deb)
Step 4: Download the libept1.4.12_1.0.12_i386.deb
Step 5: Copy the synaptic_0.81.1_i386.deb file and the libept1.4.12_1.0.12_i386.deb file from online computer into the flash drive.
Step 6: Copy the synaptic_0.81.1_i386.deb file and the libept1.4.12_1.0.12_i386.deb file from flash drive into home folder of the offline ubuntu 14.04 Trusty Tahr computer.
Step 7: open terminal by pressing [ctrl], [alt], and [T] button.
Step 8: in the terminal, type in:
```

sudo dpkg -i libept1.4.12_1.0.12_i386.deb

```
and then wait until the terminal finishes processing, the terminal should repliy like this:
```

Selecting previously unselected package libept1.4.12:i386.
(Reading database ... 164423 files and directories currently installed.)
Preparing to unpack libept1.4.12_1.0.12_i386.deb ...
Unpacking libept1.4.12:i386 (1.0.12) ...
Setting up libept1.4.12:i386 (1.0.12) ...
Processing triggers for libc-bin (2.19-0ubuntu6.5) ...

```
Step 9: in the terminal type in:
```

sudo dpkg -i synaptic_0.81.1_i386.deb

```
and then wait until the terminal finishes processing, the terminal should reply like this:
```

the terminal replied:
Selecting previously unselected package synaptic.
(Reading database ... 164428 files and directories currently installed.)
Preparing to unpack synaptic_0.81.1_i386.deb ...
Unpacking synaptic (0.81.1) ...
Setting up synaptic (0.81.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...

```
Step 10: Synaptic will have already been installed, to open the synaptic program, open terminal, and then type in:
```

synaptic

```

---

### Post by Vladlenin5000 on 2015-03-14
Why do you want to install an alternative internet-based package manager in a computer without it?
Installing Synaptic is easy enough just by downloading the *.deb and installing it as usual, but for what exactly? Anything you wanna do with it REQUIRES INTERNET!

---

### Post by newbie14 on 2015-03-14
> **Vladlenin5000 said:**
> Why do you want to install an alternative internet-based package manager in a computer without it?
What is "it"? if "it" you mentioned is "synaptic", then it is because some early forum discussion suggest that I must install synaptic. This is the suggestion post: [http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653](http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653)

> **Vladlenin5000 said:**
> Why do you want to install...
Because originally, I wanted to Install an nvidia graphic card driver to my offline ubuntu computer. This is my original thread asking for a guidance of how to do such installation: [http://ubuntuforums.org/showthread.php?t=2268330&p=13241442#post13241442](http://ubuntuforums.org/showthread.php?t=2268330&p=13241442#post13241442)

> **Vladlenin5000 said:**
> Installing Synaptic is easy enough... 
I am sorry, no matter how easy, I do not know how to install synaptic, because I am very new to ubuntu, let alone linux itself. I have never seen in my life a linux computer installs any program or anything without any internet connection. If it is easy enough for You to install synaptic, would you kindly, care to guide me every step in installing the synaptic? Is this ubuntu forum website is the correct place to search for such help or guidance? or is this not? Where should I go to get help? To whom should I ask my questions?

> **Vladlenin5000 said:**
> ...just by downloading the *.deb...
Where is the u.r.l addres for such a *.deb file, assuming the ".deb" You mentioned was a file. How to download such a *.deb file using a windows computer? I am currently on line using rented windows computer, very far away from my original, primary, offline ubuntu computer at home.

> **Vladlenin5000 said:**
> ... and installing it as usual, ....
as usual? I am very very sorry, I have never installed anything using linux. I have never installed anything using ubuntu. I have barely zero experience in installing anything in linux or ubuntu. I have never seen in my life a linux computer installs any program or anything without any internet connection. If installing something in ubuntu is something usual for you, would you kindly, care to guide me every step in installing the synaptic? How do You usually install synaptic on an offline ubuntu computer? what u.r.l address should I go to using windows computer? what hyperlink should I click? what button should I click next? what should I type next? what should I do next?

> **Vladlenin5000 said:**
> ....but for what exactly?
originally, I wanted to Install an nvidia graphic card driver to my offline ubuntu computer. Which thread I have already posted nearly a week ago: [http://ubuntuforums.org/showthread.php?t=2268330&p=13241442#post13241442](http://ubuntuforums.org/showthread.php?t=2268330&p=13241442#post13241442)

> **Vladlenin5000 said:**
> Anything you wanna do with it REQUIRES INTERNET!
I agree. That is why I am willing to travel vast distances to get an, the only place with internet connection. And while I am now connected to the internet using windows computer and a USB flash disk, what should I do to install synaptic for my ubuntu computer at home? would you care to help me, guide me every single step of the installation process?

Thank You.

---

### Post by ian-weisser on 2015-03-15
newbie14,

Vladlenin5000 fully understood that a network connectivity is not an option for you.
His  point was that you may have rather a few headaches without network  connectivity, and that Synaptic seems an unnecessary headache. An  offline machine should not have so much package churn that Synaptic is  needed to manage it. Synaptic is merely a GUI front-end to command-line  apt and dpkg tools that are already installed on your machine.

Few  (if any) volunteers here are likely type out for you a totally  detailed, button-by-button guide. That would be utterly tedious for you  to wade through, and less helpful than you might think.

Nevertheless, here are the basics of how to install any package --including Synaptic-- to an offline machine. There are many possible variations.

Step  1) Synaptic depends on several other packages, some of which may be  missing, too. Simulate the installation of Synaptic to get the complete  list of all the packages that will be needed. Write the list down. Make  sure you get each package name *exactly*. 
```
sudo apt-get install --simulate synaptic
```

Step  2) On a network-connected machine, go to [http://packages.ubuntu.com](http://packages.ubuntu.com) .  Download the .deb packages from your list onto a portable media. Ensure  your downloads are for the correct release (12.04 Precise, 14.04 Trusty,  14.10 Utopic) of Ubuntu - wrong release won't work and will waste your  time and effort.

Step 3) Put all the downloaded packages into  /var/cache/apt/archives of the offline machine so apt (the package  manager) can find them. That directory is owned by root, so you must use  sudo. If you are unsure how to move files using sudo, see 'man mv' or  'man cp' for instructions.
```
EXAMPLE - Yours will be different
sudo mv /media/my_usb_stick/ubuntu_packages/* /var/cache/apt/archives/
```

Step 4) Install the downloaded packages using apt-get.
```
sudo apt-get install synaptic
```

---

### Post by v3.xx on 2015-03-15
Maybe

[https://www.osdisc.com/products/linux/64bit/ubuntu/ubuntu-1404-lts-software-repository-64bit.html](https://www.osdisc.com/products/linux/64bit/ubuntu/ubuntu-1404-lts-software-repository-64bit.html)

But I doubt that it will include the restricted drivers your looking for.  I posted that in your other (solved) thread, don't know if you seen it.

---

### Post by acefromspace on 2015-03-15
I was in a similar situation before I got my own internt (driving long way to use interent) This is what I did: first install ubuntu on your computer (there is a choice to also update... do not choose this... do it later) The next step is to take your computer to place with internet (most will let you do this) Then run update. When update finishes, you can download extra software (programs, applications, ect) First thing you will need is "ubuntu restricted extras" This allows you to do things with videos, music, ect. This will take some time, but is worth it. Do you have laptop or desktop? I will try to help later when I get home.

---

### Post by Vladlenin5000 on 2015-03-16
There's no point in reiterating ian-weisser's points and considering what you really want to do - _Install an nvidia graphic card driver_ -, what usually is the 'bad' advice turns into a good one in your case: Run the nvidia's installer -> [http://news.softpedia.com/news/How-to-Manually-Install-the-Latest-NVIDIA-Linux-Driver-in-Ubuntu-430937.shtml](http://news.softpedia.com/news/How-to-Manually-Install-the-Latest-NVIDIA-Linux-Driver-in-Ubuntu-430937.shtml)
No need for Synaptic or any other frontend.

Why this is usually 'bad' advice for Ubuntu users? 
The packages in the Ubuntu repositories have been tested and the whole installation process is graphical and easy as clicking and the modules are automatically updated for newer kernels one usually gets with regular system updates. Of course, internet is required for downloading the drivers from the repositories.
The nvidia installer, on the other hand, requires the use of terminal, and unless you do the usual DKMS trick, you'll have to run it after each kernel change. Although this provides the latest drivers version it's also untested.

Considering _your_ target computer won't be connected to the internet it's unlikely it'll ever be updated so you can just as well install with the nvidia installer and leave it like that.
Installing Synaptic in a PC without internet just to install packages that must be downloaded from somewhere else and can be installed with the tools already present in a vanilla Ubuntu installations seems to me an unnecessary, cumbersome, redundant and utterly useless step.

---

### Post by newbie14 on 2015-03-20
1. I typed this in the terminal program:
sudo apt-get install --simulate synaptic
2. The terminal replies with this:

yggdrasil@Fulani:~$ sudo apt-get install --simulate synaptic 
[sudo] password for yggdrasil: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Package synaptic is not available, but is referred to by another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

E: Package 'synaptic' has no installation candidate 
yggdrasil@Fulani:~$

[B][screen capture]("http://i.imgur.com/m4ZGOdH.png?1")

[/B]3. I went to the internet rental, opened the ubuntu packages website:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
4. I read the terminal's reply and compared to the ubuntu packages website.
5. The terminal's reply does not contain any names of the packages required and must be downloaded.
6. I can not follow your instructions any further.

My questions:
1. What command other than 
sudo apt-get install --simulate synaptic
I must type in the ubuntu terminal to know which packages to download?

I followed your advice, and I did these steps:

[**Step 1:** ]("http://i.imgur.com/t9ItK0t.png") I opened your u.r.l hyperlink address.

[**Step 1a:**]("http://i.imgur.com/IrQDKce.jpg") I wrote down the instruction on the website to a piece of paper.

**[Step 2:]("http://i.imgur.com/Z8iGExb.png")** The website page suggest that I get a NVIDIA.run file. So I searched using google for the file.

[**Step 3:**]("http://i.imgur.com/gmtHMEu.png") I opened the first search result. I clicked, the NVIDIA website's hyperlink.

[**Step 4: **]("http://i.imgur.com/oEkpRI0.png")I selected the "download" button.

[**Step 5:**]("http://i.imgur.com/KXHORx3.png") I selected the "agree and download" button.

**[Step 6]("http://i.imgur.com/NDcPHuv.png"): **I chose the download directory on my internet rental computer.

[**Step 8:**]("http://i.imgur.com/dxjScla.png") The download completes, I have the file and copied it to my USB Flash Disk.

**[Step 9:]("http://i.imgur.com/i0jNK27.png")** I check the properties of the file, making sure the file is not broken.

[**Step 10: **]("http://i.imgur.com/pCSD9pw.png")I pasted the NVIDIA...run file to my ubuntu computer at home, I pasted it at the home folder.

**Step 11: **I pressed the [CTRL] + [ALT] + [F1] button on my keyboard, and a full-screen terminal appears.

[**Step 12:**]("http://i.imgur.com/tbcOQw7.jpg") I looked at my physical paper note, and typed in the commands written.

[IMG]http://i.imgur.com/tbcOQw7.jpg[/IMG]

From this result. I think the installation attempt has failed.
They suggestion at post number 7 (#7 or the [http://ubuntuforums.org/showthread.php?t=2269294&p=13246591#post13246591](http://ubuntuforums.org/showthread.php?t=2269294&p=13246591#post13246591) ) is not the answer of my main question.
My questions are:

1. Which step did I do wrong?
2. Is there a .run for NVIDIA linux-x86 installer file I can download?
3. If there is an .run installer file for Linux-x86, where is it located? at what u.r.l address is that file located?

---

### Post by ian-weisser on 2015-03-20
> **newbie14 said:**
> What command other than 
sudo apt-get install --simulate synaptic
I must type in the ubuntu terminal to know which packages to download?

Your package database is not set up yet.
See [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository) for how to do that.

---

### Post by newbie14 on 2015-03-20
Heck, what can I do, then? some dude who had more experience at ubuntu told me to install synaptic, as shown here:
[http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653](http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653)
so I tried to do it anyways.
But the problem is, I don't know how to do his suggestion (install the synaptic), so I posted this thread, asking how to do it. But, oh well, if
> **Vladlenin5000 said:**
> 
Installing Synaptic in a PC without internet just to install packages .... seems to me an unnecessary, cumbersome, redundant and utterly useless step.
then that suggestion by user: 9d9 at
[http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653](http://ubuntuforums.org/showthread.php?t=2268330&p=13241653#post13241653)
> **9d9 said:**
> The easiest way is to first: install synaptic, then...
is a whack.

Now that I've got my curiosity in how to install a synaptic on an offline ubuntu computer. What should I do to install synaptic on my offline ubuntu computer?

> **ian-weisser said:**
> Your package database is not set up yet.
See [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository) for how to do that.

I have opened the
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
website.
[**Screen Capture of the website**]("http://i.imgur.com/treA0nO.png")

The website instructed me to do "release" at step number 1.
But I don't know what "release" is.
What should I do?
What is this "Release" means in the website?

I opened the first 2 hyperlinks provided in the web. They are:
[**1. The first hyperlink:**]("http://i.imgur.com/cr8C6Zg.png") [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)
a web page appears like
[**this.**]("http://archive.ubuntu.com/ubuntu/dists/")
I thought maybe "release" is a name of a folder I should download.
So I hit control + F and typed in "release" on the search text box.
But it found
[**nothing.**]("http://i.imgur.com/tBwsjWw.png")

2. The second hyperlink, the "suite codename" is just a
[**cirular reference**]("http://i.imgur.com/dqlAAX2.png")
linking to it's own web page.

This really really confuses Me.
This hyperlink You provided (user: [COLOR=#000000]ian-weisser) [/COLOR]:
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
does not explain the specific steps for how to "do that".
this web page has failed to help me.

This raises even more questions than answers.

my question is:
1. Is there anything else I can do to install synaptic on my offline ubuntu computer?
[**2. How to set up my package database?**]("http://ubuntuforums.org/showthread.php?t=2270130&p=13249306#post13249306")

---

### Post by Mark Phelps on 2015-03-20
The person who told you to install Synaptic presumed you were then going to use Synaptic to obtain and install the drivers -- which you apparently are NOT going to do.

As Vladlenin5000 already indicated, installing Synaptic in your case is > an unnecessary, cumbersome, redundant and utterly useless step. 

You're going about this the wrong way -- what you need is the 32-bit driver file, but since I don't use Nvidia graphics, I don't know where to tell you to find it.  You would do better asking folks about where to get that file.

---

### Post by Ko_Char on 2015-03-20
For offline packages, there is an app called Camicri Cube. I haven't tried it myself since I've the Internet access all the time. 
Some people from my home country say it is good. Give it a try. 

[https://launchpad.net/camicricube](https://launchpad.net/camicricube)

---

### Post by newbie14 on 2015-04-17
Seriously everyone, please. What should I do to install synaptic to my offline ubuntu computer?
what website can I download the synaptic installation files?
what is the name of the synaptic installation files?
what is the format of the synaptic installation files? .deb? .run? .tar.gz?

---

### Post by flaymond on 2015-04-17
I don't know if I could help you, but you can view the software caches in the terminal or installing from Ubuntu Software Center. To view the caches just type in the Terminal -

```
apt-cache search synaptic
```

You can change the synaptic to any software you want to see. Anyway, why do you want to install Synaptic? Synaptic is package manager, mostly for installing, uninstalling, finding, replacing or generally, it's managing your packages. From the old thread you started, your main purpose is to install Nvidia Card Driver, and by that for what purpose? Anyway, where are you connected while starting this thread? Why you don't bring your Ubuntu laptop's to the 'Internet Zone'. It's also good to know, that you familiar with Ubuntu Forums BB codes. Thanks.

---

### Post by MAFoElffen on 2015-04-17
For nvidia... Tell me the info from:
```

sudo lshw -n -c video

```
That would tell me the pertinent model info to determine which driver you needed.

The driver packages for nvidia drivers are not just a single package. It has a "certain" (dependent on the model and what range that model fits into) main package that will in turn install dependent packages. 

With the above info, in turn, I'll put together a list of the packages you need to download and the launchpad links the those...

It's not magic... I do that several ways... Via Lauchpad, looking at the dependencies needed for that package... querying from apt-get (using the simulation/test flag) or via Synaptic, by marking the package for installation and looking at which packages it says that it will install.

So, yes... even though others say it would be irrelevant to install synaptic... It can be used as a diagnostics tool. But it is just one of many that could be used to determine what you need...

In fact, you could determine that easily yourself via doing (using this as an example package name)
```

sudo apt-get install --install-recommends -s nvidia-common

```
... the "-s" flag tells it to simulate...
In that simulation, it would look at what is installed, determine which packages it would need to download from where, to do that install of the example package nvidia-common.

---

### Post by newbie14 on 2015-04-17
> **InterProg said:**
> ```
apt-cache search synaptic
```
Thank you very much for your instruction. I will try later it as soon as I get home. And come back with the results.

> **InterProg said:**
> why do you want to install Synaptic? Synaptic is package manager, mostly for installing, uninstalling, finding, replacing or generally, it's managing your packages.
My interest had shifted from "how to install nvidia graphics card driver to an offline ubuntu computer" to "how to install synaptic on an offline computer. There is a post in this forum (I will add the u.r.l hyperlink later) questioning what to do to his/her ubuntu computer which will be relocated and will be offline for a long time, and one of the replies in that thread suggest that he / she must install synaptic first. Because synaptic can create a script of what to download if one day he/she want to install something on his/her ubuntu computer, and save the script to a flash drive, bring the flash drive with the installation script to a computer which connected to the internet. And even download the installation files to the flash drive so he/she can bring the flash drive home and do an offline installation. His/her situation matches exactly with my situation. The only difference is that he/she can install synaptic while still connected to the internet, while my ubuntu computer is not connected to internet. That thread amplifies my curiosity to find out how to install synaptic on an offline ubuntu computer.

> **InterProg said:**
> your main purpose is to install Nvidia Card Driver, and by that for what purpose? I have somewhat fulfilled my original purpose. I have known what to type in the terminal to install the graphics driver without internet connection. What I must do now, is only to find the correct file to download, I have tried 2 out of 100-200 files to choose from, so far I haven't found the correct installer file yet, but that doesn't matter because now I know what to do with the .run installation files, and what to type in the terminal to install the file. Meanwhile, while I try install each .run installer file, I shift my experiment / interest to "how to install synaptic on an offline ubuntu computer. For the purpose, there is a very cool desktop / window visual effect in ubuntu when, if a window is dragged, the window box moves with a jelly-like movement. And when a window closed, the window box will "explode" like spraying copious amount of glowy glitters, and the window appeared shattered to many pieces like a glass would shatter. I assume, that visual effect would require an installation of graphic card driver.

> **InterProg said:**
> Anyway, where are you connected while starting this thread? Why you don't bring your Ubuntu laptop's to the 'Internet Zone'. It's also good to know, that you familiar with Ubuntu Forums BB codes. Thanks. I am currently at an internet computer rental shop at a nearby town next to my home town. This internet computer rental shop uses windows operating system. I cannot bring my ubuntu computer anywhere because it is not a laptop, my ubuntu computer is a mid-tower desktop computer and very very fragile. The casing is welded tight on a wall. If I try to detach the computer, the computer and the wall will be broken. And all the screws of the computer casing uses are broken and cannot be turned loose with any screwdriver, putting rubber between the screw and the screwdriver also doesn't help. Getting a u.s.b modem is also impossible, as it is very very expensive. There is also zero signal reception to 2G / 3G network signal reception at my home. In short, getting my ubuntu computer to an internet connection is simply impossible. All it (my ubuntu computer) can do to communicate outside the box is using two usb slot.

> **MAFoElffen said:**
> ```

sudo lshw -n -c video

```
That would tell me the pertinent model info to determine which driver you needed.

[QUOTE=MAFoElffen;13266736]
```

sudo apt-get install --install-recommends -s nvidia-common

```

Thank you very much for your instructions. I will try it later as soon as I get home. And come back with the results.

---

### Post by newbie14 on 2015-04-18
I have typed
```
apt-cache search synaptic
```
and the terminal replied:
```
xserver-xorg-input-synaptics-lts-utopic - Synaptics TouchPad driver for X.Org server
sessioninstaller - APT based installer using PackageKit's session DBus API
```


And then I typed
```
sudo lshw -n -c video
```
and then, the terminal replied:
```
Hardware Lister (lshw) - B.02.16
usage: lshw [-format] [-options ...]
       lshw -version


    -version        print program version (B.02.16)


format can be
    -html           output hardware tree as HTML
    -xml            output hardware tree as XML
    -short          output hardware paths
    -businfo        output bus information


options can be
    -class CLASS    only show a certain class of hardware
    -C CLASS        same as '-class CLASS'
    -c CLASS        same as '-class CLASS'
    -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
    -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
    -quiet          don't display status
    -sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
    -numeric        output numeric IDs (for PCI, USB, etc.)

```


And then I typed
```

sudo apt-get install --install-recommends -s nvidia-common

```
And then, the terminal replied:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ubuntu-drivers-common' instead of 'nvidia-common'
ubuntu-drivers-common is already the newest version.
ubuntu-drivers-common set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

what should I type next?

---

### Post by ian-weisser on 2015-04-18
> **newbie14 said:**
> I have typed
```
apt-cache search synaptic
```
and the terminal replied:
```
xserver-xorg-input-synaptics-lts-utopic - Synaptics TouchPad driver for X.Org server
sessioninstaller - APT based installer using PackageKit's session DBus API
```

Okay, so you system does not seem to have the 'universe' repository enabled. (Irrelevant - your system is offline)
And your system doesn't know about the 'synaptic' package (Expected, unless you followed the instructions in post #4 above)

Post #4 above told you how to install Synaptic to your offline system. Detailed instructions you claim to want. Four weeks ago. Have you tried it?

---

### Post by newbie14 on 2015-04-18
what should I type next?
what file should I download?
what file should I copy to the home folder of my offline ubuntu computer at home?

---

### Post by newbie14 on 2015-04-18
wait,... let me see...

---

### Post by newbie14 on 2015-04-19
I have typed:
```
sudo apt-get install --simulate synaptic
```

And the terminal replied:
```
[sudo] password for fulani: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'synaptic' has no installation candidate
```

Any advice?

---

### Post by CantankRus on 2015-04-19
Enable the universe repo.
```
software-properties-gtk
```
but as **ian-weisser** said your offline so no point anyway.

Don't you have a friend or family member's home you can take your computer to and connect to the internet?
Then all you need do is type "additional drivers" in the dash and then install the latest nvidia driver 
which I believe is what you are trying to achieve.

---

### Post by newbie14 on 2015-04-19
> **CantankRus said:**
> Don't you have a friend or family member's home you can take your computer to and connect to the internet?
No, the nearest family member is 200 kilometers away from my home. My ubuntu computer at home cannot be taken anywhere, and connecting my ubuntu computer to an internet is impossible. my ubuntu computer is a mid-tower desktop computer and very very fragile. The casing is welded tight on a wall. If I try to detach the computer, the computer and the wall will be broken. And all the screws of the computer casing uses are broken and cannot be turned loose with any screwdriver, putting rubber between the screw and the screwdriver also doesn't help. Getting a u.s.b modem is also impossible, as it is very very expensive. There is also zero signal reception to 2G / 3G network signal reception at my home.

---

### Post by mc4man on 2015-04-19
run & post 
```
sudo lshw -c display
```
From that the proper nvidia driver package & any packages it depends  can been figured out.
Then you would download all of them to a folder on your flash drive, bring it home. The drive  would be inserted in your Ubuntu machine, you'd cd to the containing folder & install all the packages at once with dpkg. (sudo dpkg -i *.deb

Edit : it would also be better if you were using a supported Ubuntu release, I'd consider 12.04 or maybe 14.04 depending on your hardware..

---

### Post by ian-weisser on 2015-04-19
> **newbie14 said:**
> ```
E: Package 'synaptic' has no installation candidate
```

Well, sorry about that. Synaptic is in the Universe repo.

Here's what happens when I simulate installing Synaptic, which I don't have installed (I use different tools). Your mileage may very.
```
$ sudo apt-get install --simulate synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libept1.4.12
Suggested packages:
  dwww deborphan tasksel
[B]The following NEW packages will be installed:
  libept1.4.12 synaptic[/B]
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Inst libept1.4.12 (1.0.12 Ubuntu:14.10/utopic [amd64])
Inst synaptic (0.81.2 Ubuntu:14.10/utopic [amd64])
Conf libept1.4.12 (1.0.12 Ubuntu:14.10/utopic [amd64])
Conf synaptic (0.81.2 Ubuntu:14.10/utopic [amd64])

```

So if my system were offline, I would need to:
1) Know which version of Ubuntu I am running (I am running 14.10, Utopic Unicorn)
2) Go to [http://packages.ubuntu.com](http://packages.ubuntu.com)
3) Download the the packages **libept1.4.12** and **synaptic** for my version of Ubuntu. Save them on a removable media.
4) Transport the removable media to my offline computer.
5) Install the packages in the correct order (dependency first). Apt may not work since you are both offline and have no Universe packages in your local database.
```
sudo dpkg --install /the/path/to/wherever/you/saved/**libept1.4.12**_1.0.12_amd64.deb
sudo dpkg --install /the/path/to/wherever/you/saved/**synaptic_0.81.2**_amd64.deb
```
Your version numbers may be slightly different. You might be running a different version of Ubuntu than I am.
If you're running an obsolete or unsupported version of Ubuntu, then this won't work at all - the packages won't be available on the website.

That's it. I open my dash and search for Synaptic, and it is there...ready to work.

---

### Post by newbie14 on 2015-04-19
> **ian-weisser said:**
> Synaptic is in the Universe repo.
what is universe repo?

I am running ubuntu 14.04 trusty.
Can synaptic be installed on ubuntu 14.04 trusty?

---

### Post by ian-weisser on 2015-04-19
> **newbie14 said:**
> what is universe repo?
See [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

> **newbie14 said:**
> Can synaptic be installed on ubuntu 14.04 trusty?
Yes. 14.04 is a supported version of Ubuntu until April 2019.
See [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by newbie14 on 2015-04-20
> **ian-weisser said:**
> Yes. 14.04 is a supported version of Ubuntu until April 2019 [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I have some questions:
1.How to install synaptic on an offline ubuntu 14.04 Trusty computer?
2.what should I type in the terminal next?
3.what .deb file should I download?
4.what file should I copy to the home folder of my offline ubuntu computer at home?

your code:
sudo apt-get install --simulate synaptic
and
sudo apt-get install synaptic
had failed to install synaptic to my offline ubuntu 14.04 Trusty Tahr computer.

---

### Post by CantankRus on 2015-04-20
Type this in a terminal , press enter and post the output
```
uname -a
```
eg
```
**[COLOR="#008000"]glen@Trusty:~$[/COLOR] uname -a**
Linux Trusty 3.16.0-33-generic #44~14.04.1-Ubuntu SMP Fri Mar 13 10:33:29 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

and I will give you links to the two files you need to download.

> **newbie14 said:**
> I have some questions:
1.How to install synaptic on an offline ubuntu 14.04 Trusty computer?
2.what should I type in the terminal next?
3.what .deb file should I download?
4.what file should I copy to the home folder of my offline ubuntu computer at home?

your code:
sudo apt-get install --simulate synaptic
and
sudo apt-get install synaptic
had failed to install synaptic to my offline ubuntu 14.04 Trusty Tahr computer.
Seriously, are you reading any of the comments.
Additional software is installed from Ubuntu's repositories over the internet.
You aren't connected so you can't install anything with "sudo apt-get install"

What you can do though is download the deb file for synaptic and another dependency file using an online machine to a usb stick.
To get links for the deb files we need your ubuntu release and architecture to get the correct files.
The above **uname -a** command will give this info.

---

### Post by newbie14 on 2015-04-20
I have typed
```
uname -a
```
in the terminal.
And then, the terminal replied:
```
Linux Kompie 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:45:15 UTC 2015 i686 i686 i686 GNU/Linux
```
Thank you for your help and instructions by the way, user CantankRus

---

### Post by CantankRus on 2015-04-20
Here's links to the two files. Total dowload size is about 1.5Mb
```
http://mirrors.kernel.org/ubuntu/pool/universe/s/synaptic/synaptic_0.81.1_i386.deb
http://mirrors.kernel.org/ubuntu/pool/main/libe/libept/libept1.4.12_1.0.12_i386.deb
```
Copy and paste the links to a text file on a usb stick, then copy and paste each link in the web browser of an online machine to download.
Transfer the deb files to the usb stick.

Get back once you're done.
Is the purpose of installing synaptic to get nvidia drivers?
If that is the case you can then use synaptic to make a list of all the files you need to install nvidia-current and go back to the online machine and download.
Does the online machine run ubuntu or windows?

PS Trying the synaptic method because, although the method you tried in [**_[COLOR="#B22222"]Vladlenin5000's #7 post[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2269294&p=13246591#post13246591") should be easier, I could not get it to work.

---

### Post by newbie14 on 2015-04-20
Thank You very much user CantankRus, let me see...

---

### Post by newbie14 on 2015-04-20
Thank you very much user CantankRus, synaptic has been successfully installed because of your instructions, You sir, are awesome.

Currently, the purpose of installing synaptic are to:
1. Get Nvidia drivers. And install said drivers to an offline ubuntu 14.04 "Trusty Tahr" computer.
2. Install Gimp image editor to an offline ubuntu 14.04 "Trusty Tahr" computer.

These purpose may evolve larger in the future. Possibly to also install many many more programs to an offline ubuntu 14.04 "Trusty Tahr" computer.

The online machine runs windows 7 operating system only.

Now that [**I have installed synaptic like this**]("http://i.imgur.com/UymmvJF.jpg"), I have one more question...
1. What menu should I click on the synaptic to make a list of all the files I need to install nvidia-current?

---

### Post by CantankRus on 2015-04-20
Firstly check your sources.
In a terminal run...
```
software-properties-gtk
```
and check you have the 4 repos **enabled** and the cdrom **disabled**.
[ATTACH=CONFIG]261421[/ATTACH]
It may ask to reload. Reload even though it will give you an error because you are offline  but it will remove the cdrom from your sources.
Wait for it to complete then close if still open.

Open synaptic using the terminal not from an icon as you want it to run as a normal user
to make it easier to save the package download script.
In terminal ...
```
synaptic
```
Search for nvidia-current ...right click on it and "mark for installation".
[ATTACH=CONFIG]261422[/ATTACH]

Then mark additional required changes in the next dialogue.
[ATTACH=CONFIG]261423[/ATTACH]

Go to File > Generate package download script
[ATTACH=CONFIG]261424[/ATTACH]

...and save to your home folder as something descriptive like nvidia-downloads
[ATTACH=CONFIG]261425[/ATTACH]
Close synaptic and quit.

The script should look similar to this(yours will different)....
```
#!/bin/sh
wget -c [COLOR="#FF0000"]**http://archive.ubuntu.com/ubuntu/pool/main/libv/libvdpau/libvdpau1_0.7-1_amd64.deb**[/COLOR]
wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/e/eglibc/libc6-i386_2.19-0ubuntu6_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-304/libcuda1-304_304.117-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/g/gccgo-4.9/lib32gcc1_4.9-20140406-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-304/nvidia-304_304.117-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-304/nvidia-current_304.117-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-304/nvidia-libopencl1-304_304.117-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-304/nvidia-opencl-icd-304_304.117-0ubuntu1_amd64.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.17.1_all.deb
wget -c http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_331.20-0ubuntu8_amd64.deb
```
If your online machine was running Linux you could just run the script to download all the packages.
In windows just copy and paste [COLOR="#FF0000"]**each link**[/COLOR] in your web browser to download the deb files.

Move the downloads to a usb stick and transfer them to your home folder on the offline machine.
In the terminal run ...
```
sudo dpkg -i *.deb
```

After installation you may want to move the deb files to another folder or delete  to unclutter your home folder.
If you delete files on a usb stick they will remain as hidden files on the usb until you empty trash.
If you need space on the usb stick, after deleting files on the stick make sure to empty trash before disconnecting the usb.

If you need to revert back to open source drivers...
```
sudo apt-get purge nvidia*
```

---

### Post by newbie14 on 2015-04-20
> **CantankRus said:**
> Firstly check your sources.
In a terminal run...
```
software-properties-gtk
```
and check you have the 4 repos **enabled** and the cdrom **disabled**.
[ATTACH=CONFIG]261421[/ATTACH]
It may ask to reload. Reload even though it will give you an error because you are offline  but it will remove the cdrom from your sources.
Wait for it to complete then close if still open.

Open synaptic using the terminal not from an icon as you want it to run as a normal user
to make it easier to save the package download script.
In terminal ...
```
synaptic
```
Search for nvidia-current ...right click on it and "mark for installation".
[ATTACH=CONFIG]261422[/ATTACH]


I have successfully done well so far
[**like this,**]("http://i.imgur.com/UQdP0Az.jpg")
[B][and like this,]("http://i.imgur.com/Ar76cO8.jpg")
[/B]But at the next step where I search for Nvidia current, (using the search bar) the synaptic did not find any match.
like this.
[ATTACH=CONFIG]261434[/ATTACH]
And I can only follow until this step, I cannot follow further step from here.
Any advice?

by the way, I really appreciate your effort in providing screen-captures, many thanks man.

---

### Post by CantankRus on 2015-04-20
> **newbie14 said:**
> I have successfully done well so far
[**like this,**]("http://i.imgur.com/UQdP0Az.jpg")
[B][and like this,]("http://i.imgur.com/Ar76cO8.jpg")
[/B]But at the next step where I search for Nvidia current, (using the search bar) the synaptic did not find any match.
like this.
[ATTACH=CONFIG]261434[/ATTACH]
And I can only follow until this step, I cannot follow further step from here.
Any advice?

by the way, I really appreciate your effort in providing screen-captures, many thanks man.

Yeah I don't know... maybe you need to be online to have the proprietary drivers listed.

Try creating a download script for something else you want to install.


Also for drivers I just tested [**_[COLOR="#B22222"]this guide[/COLOR]_**]("http://ubuntuhandbook.org/index.php/2015/01/install-nvidia-346-35-ubuntu-1404/") and it worked. I am now running the 346.35 nvidia drivers.  
For step 3 in the guide, instead of "**gksudo gedit**" use ...
```
**sudoedit** /etc/modprobe.d/blacklist-nouveau.conf
```
paste in the 5 lines shown then press "ctrl+x" followed by "y" then "Enter".

You will get a warning at the start of install that something didn't work but just continue on.
For the install commands to work the dowloaded nvidia ".run" file must be in your **Downloads** folder.

---

### Post by oldos2er on 2015-04-20
> **newbie14 said:**
> Currently, the purpose of installing synaptic are to:
1. Get Nvidia drivers. And install said drivers to an offline ubuntu 14.04 "Trusty Tahr" computer.
2. Install Gimp image editor to an offline ubuntu 14.04 "Trusty Tahr" computer.


Synaptic can't install from local packages, it only looks to online repostories. However, gdebi or dpkg can install from *.deb files you've downloaded, assuming all dependencies are met.

I should add, dpkg is already installed on Ubuntu, but gdebi is not. dpkg is a terminal program, gdebi is GUI; so you will need to determine which you might prefer.

---

### Post by CantankRus on 2015-04-20
> **oldos2er said:**
> Synaptic can't install from local packages, it only looks to online repostories. However, gdebi or dpkg can install from *.deb files you've downloaded, assuming all dependencies are met.

I should add, dpkg is already installed on Ubuntu, but gdebi is not. dpkg is a terminal program, gdebi is GUI; so you will need to determine which you might prefer.
Using synaptic to create a package download script and dpkg to install is I think what was meant.

---

