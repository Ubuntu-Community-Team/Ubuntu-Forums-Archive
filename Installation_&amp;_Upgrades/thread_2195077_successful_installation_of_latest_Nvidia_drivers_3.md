---
title: "successful installation of latest Nvidia drivers 319 on Ubuntu 12.04 LTS"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by manishkumarsharma. on 2013-12-22
First of all Hey guys ):P 'm so happy to be here . This is gonna be my first post . Well, I wanted to say hi to the Ubuntu community first. 
Now, I am a complete beginner to Ubuntu (hardly a week since I have tried **Ubuntu 12.04** ). Well, for a complete beginner like me, having no previous Linux experience, I had to face a lot of bumps along the road. Now Ubuntu is great!!, but no offence ,I am gonna say it- For a noob like me, Ubuntu has given me a really hard time for the installation process, leave the learning curve alone. 

Right now I have been able to successfully install Ubuntu 12.04 LTS with WORKING Nvidia 319 updates !!! I am gonna share my experience present a sort of tut for the first timers.

My Hardware :
[B]Model: Dell  XPS L501X
OS type : 64 bit
Processor : Intel® Core™ i3 CPU M 380 @ 2.53GHz × 4 
Graphics Card : Nvidia GTX 420M(with Nvidia Optimus)

Problem : [/B]Iwould [B]say is "unable to have working Nvidia drivers due to unconfigured configuration file "
[/B]I have been through all the forums and Q&A sites and I wouldn't say that there was no solution to this problem (I am really not taking credit for any of this), I am just compiling the precise working solution here .

For complete beginners, there is default **nouveau driver** installed in Ubuntu at the fresh start , You might give in to the temptation of fooling around and installing the available proprietory Nvidia driver form the **Additional Drivers** location but not yet, stop!! and just follow the steps and you can avoid all the trouble that I had to go through. Just as consequence(You might have already screwed up probably) ,you will end with an unbootable system with black screen(in my case it was the black screen followed by "Broke pipe ,couldn't write Bytes" message). Well, I found out that this unable to load Nvidia driver and already unloaded Nouveau driver .
In case you already have unbootable system, I would recommend reinstalling Ubuntu again .But why even let this happen, just follow the steps here .
Things you need :
1) Timeshift : This is a perfect tool for creating backup without any hassle, and restoring later .Download it here : [http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html) . It will come in handy in case you screw up. Just create the snapshot on another drive(not your Ubuntu installation drive).
2)Synaptic Package Manager : Need I appreciate it, its given you know how to use it.(Download it from Software centre)
3)Patience : Of course!
**Goal** : To install the Nvidia 319 updates(rather than 304 which do not have native support for Optimus).

**Note**:Nvidia 304 updates are included in nvidia-current or nvidia-current-updates and Nvidia 319 is the bleeding edge latest update.
First of all have a live CD/live USB with Ubuntu 12.04 LTS ready . Now, install Ubuntu. Just so that no dependency problem occurs , install all the updates with update manager.
1)Create a snapshot now 
2)Now we are gonna prepare fo the installation of the Nvidia 319 drivers,
Execute : 
```
sudo apt-get install build-essential
```
```
sudo apt-get install linux-source
```
```
sudo apt-get install linux-headers-generic
```
Above code is common for Both Terminal way and Synaptics way because Headers are not included by default in Ubuntu 12.04 LTS
3)Take another screenshot and if screwed up later start by recovering from this screenshot.
Now download the 319 update as a debian package(So that you don't have to download it every time you screw up),here [http://packages.ubuntu.com/precise-updates/amd64/nvidia-319-updates/download](http://packages.ubuntu.com/precise-updates/amd64/nvidia-319-updates/download) from any mirrors and save it in another drive.(Download only if you are going Synaptics way)
4)Terminal way:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install nvidia-current-updates-dev
or   sudo apt-get install nvidia-319-updates
```
```
sudo apt-get install nvidia-settings-319-updates
```
```
sudo apt-get install nvidia-common
```
5)Synaptics Way :
Well,just add downloaded Nvidia 319 package and install it.It's gonna automatically take care of the dependencies and nvidia-settings-319 package installation.
6)Now restart the system.
7)Go to Dash, open Nvidia and What! still it's gonna show that **No Drivers have been activated**. Now go to the **additional drivers** location and activate the Nvidia post release update, wait a minute or two and Voila! its acctivated.
8)Now, if you have successfully activated, you should see something like this:
[ATTACH=CONFIG]248808[/ATTACH]

9)Now again go to Dash, open Nvidia again,you should see something like this :
[ATTACH=CONFIG]248809[/ATTACH]
10)Most importantly,assuming you have been successful up till here, go ahead and create another snapshot right now, cuz' this is working state and who knows you might find yourself installing Ubuntu again for any other bug or whatever.
11)To test that Ubuntu is using Nvidia driver or not type :
```
sudo /sbin/lsmod | grep nvidia
```
You should see something like this :
[ATTACH=CONFIG]248810[/ATTACH]

I did not use to create Backups in Windows(to free space) but I am gonna do it cuz. all this struggle has taught me the importance of backups.
[B]
Btw[/B] : If any of above step shows already installed or any other sort of problem ,for instance nvidia-common might be already installed or doesn't work ,try shuffling the given step with +- 2 steps ,for it might be a dependency issue. But I highly recommend going the Synaptic way. If you have already installed 304 update and updating on top of that, your new screen resolution is gonna be stuck at 1024*768(mine did) .You'r gonna have to edit the lightdm.conf in /etc/lightdm/ .Google it.
Never install the proprietory Nvidia drivers directly.
And all the steps you have followed  for 319 can also be followed for 304 or nvidia-current ,with just a slight bit of change in commands.Synaptics is again welcome.
For any experimentation stuff , you are always advised to create snapshot before making any amend.

At last I would like to give credit to many sources:
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)
[http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-nvidia.html)
[http://askubuntu.com/questions/334902/12-04-update-and-nvidia](http://askubuntu.com/questions/334902/12-04-update-and-nvidia)
[http://askubuntu.com/questions/291199/ubuntu-13-04-installation-nvidia-driver](http://askubuntu.com/questions/291199/ubuntu-13-04-installation-nvidia-driver)
[http://askubuntu.com/questions/291199/ubuntu-13-04-installation-nvidia-driver](http://askubuntu.com/questions/291199/ubuntu-13-04-installation-nvidia-driver)

If I have left out any step(if you think) or anything doesn't work please do tell me.

---

### Post by TheFu on 2013-12-22
Fantastic that you are here and trying to help others! Thanks!

Just be aware that whenever you install anything either from a download or with a specific number in it from the repositories, then you have just accepted the responsibility to maintain that package going forward ... which sorta defeats the purpose of using a package manager, IMHO.  

TL;DR - but if you did get nvidia drivers directly from nvidia, then that just broke the automatic update methods and likely will break somehow the next time a new kernel is released.  nvidia-current is probably the package that most people want to install.

---

### Post by lzxiaohu on 2014-04-13
Thank you! Because your post helps me solve the black problem.

---

### Post by kilua2 on 2014-04-18
Hello,

First at all thank you for your tutorial.

I followed all your steps but at the moment to select the appropiate driver (step 7) I do not have the same than you do, in the screenshoot for the step 7 you have "NVIDIA accelerated graphics driver (post-release....)", however I don't have that driver. The only drivers related to nvidia are "nVidia Riva/TNT/GeForce" and "Framebuffer driver for nVidia graphics chipset". Did you know something about this?

Regars,

---

### Post by woodllan on 2014-07-21
It solved my problem! Thank you so much!

I upgrade my ubuntu 12.04 last week. It turned out fine right after that.
However, I stuck at welcome screen (screen with only desktop background).
When I reinstalled nvidia drivers, simply:
sudo apt-get install nvidia-current
I had X worked but lost my twinview since in the additional drivers I have 'drivers activated but not in use'.
And your method solved it!
Thank you very much!

---

### Post by C07C03 on 2014-07-29
Hi,
has anyone tried to install nvidia drivers on this hardware in Ubuntu 14.04? I've got a fresh install of Ubuntu Gnome 14.04 and no matter what I tried, my system freezes before login every time I install nvidia drivers.
I tried Nvidia 319 and 331, via terminal and via synaptic.

---

