---
title: "Install the newest nVidea driver for Lucid Lynx 10.04"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by Cavsfan on 2012-03-27
I know there is a PPA for getting new nVidia drivers but, I like this method as I can have the latest driver quicker.

I am pretty sure this will work for other versions of Ubuntu besides 10.04. I know it has worked for a few people using Ubuntu 12.04.
The latest nVidia driver came out for Linux on 2012.05.16 version 295.53.
This is not for the squeamish, so if you are not comfortable doing this or are new to Ubuntu I would not recommend it.

[[COLOR=blue]_Download the latest nVidia driver here._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")
This is the English version, but you can select another language I am sure.
You will select either the 32 bit Linux or 64 bit Linux version.

Here are the instructions for installing the driver:
[[COLOR=blue]_http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html_[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html")
I have used this many times without any problems. I suggest printing steps 4 through 8 to have after rebooting.
I just copy them to a gedit record and print that page.  
If you have done this before you will start at step 4 as the previous steps have already been accomplished.
If you have installed the driver this way before, you will just reboot into recovery and select the shell prompt (the bottom option on my system).
The first time installing the driver after removing the default driver, you will not need to enter **telinit 3**, but the 2nd, 3rd, etc. you will need to.
The directions do not mention this but, you will want to enter **telinit 3** (the nVidia driver will tell you to do this if you do not do it now) before logging in (Step 6) and wait a few seconds for that to take effect.
Then just enter your userid and password.
Step 7 you will change the file name to the one you downloaded.

You will be asked to accept the terms and need to answer a few other questions with yes.
It will ask if you want to create a new Xorg file and you want to say yes.
Once you do step 8 to start GDM, you will be looking at your normal login screen.

After doing this, you **must** go by the following tutorial to install the driver into future kernels that are installed.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")
This was written by **sdennie** from this forum. It was written back in 2007 but, still works flawlessly.

I recommend using command line to get updates **sudo apt-get update && sudo apt-get upgrade**. 
**ranch hand**, a knowledgeable guy in this forum told me to use these commands. This way you can see what is going on. I just use Update Manager to review the updates.
If there is a kernel to be installed it will be held back and once you get the updates from the above command, you will enter **sudo apt-get dist-upgrade** to install the new kernel.
This way when installing a kernel you will see **Building NVIDIA driver for kernel .....**
And then either **SUCCESS: Driver installed for kernel ...** or **FAILURE: See /var/log/nvidia-installer.log**
If it is just upgrading a kernel it will tell you the driver is already installed.

In the future, you can either continue using this driver or update to a newer one. 
These instructions will still apply.

---

### Post by Cavsfan on 2012-03-30
I should mention that this action will render your older kernels useless. Unless you remove and re-install them. 
If you have accomplished the HOWTO (3rd link) that is.

[COLOR="Red"]I will also mention that if you have gone by the Tutorial in my signature for creating a customized Grub2 screen, 
the custom Ubuntu entry will use the last installed kernel and not the highest numbered kernel.
So, if you removed and re-installed an older kernel, that kernel will be the one that gets used at boot time.[/COLOR]

I first install the new driver into the kernel I am using.

I keep 2 kernels and what I do is I remove the older one and re-install it. If I see "SUCCESS" I know it worked.
These are the commands I used:

**sudo apt-get purge linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic**

When you purge the kernel, you will see a message that a folder was not deleted pertaining to that kernel 
because it had the nvidia-driver in it. I manually delete that folder myself before re-installing the kernel to force 
it to rebuild the driver in the kernel.

Then after that is completed without rebooting I re-install it:

**sudo apt-get install linux-headers-2.6.32-39 linux-headers-2.6.32-39-generic linux-image-2.6.32-39-generic**


Then, without rebooting, to make the newest kernel the one that boots up. I remove and re-install the latest kernel with these commands:

**sudo apt-get purge linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic**

You will notice that in addition to those three files, **linux-headers-generic** and **linux-image-generic** are also removed.

So, I enter this to re-install it:

**sudo apt-get install linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic linux-image-2.6.32-40-generic linux-headers-generic linux-image-generic**

Then both of my kernels have the new driver installed in them and my custom Grub2 menu uses the latest kernel.

---

### Post by Cavsfan on 2012-04-24
if anyone is interested, driver version 295.40 which was added 2012.04.11.
I am going to install that myself.

---

### Post by Cavsfan on 2012-04-24
Also, I should not have put Lucid Lynx in the title of this thread as it should work for all versions of Ubuntu.

---

### Post by Mike_tn on 2012-04-25
Do you get better results doing this manually? I'm running Precise for the first time, fresh Ubuntu install after being only on Debian Squeeze a long time so I have no Ubuntu packages in archives and the Ubuntu version of 295.40 nvidia-current will not install properly, maybe it's a bug in Unity, not sure. Easy fixes such as unity reset do not work.  My screen behavior seemed to match someone else who fixed it by installing the previous Ubuntu version of nvidia-current which uses 295.33 however I cannot find a download to that anywhere, I can only find the manufacturer version of that. Hence I read your post. Very detailed and easy to follow really. Makes perfect sense with everything I have read and tried in the last two days.  I'm only half-way a geek.  I would prefer to find the Ubuntu version of the driver but that could be a bad idea, you may have less bugginess cropping up doing it your way, I don't have enough experience to know. But it is also just plain fun to make computers work for you even if the advantage is only slight. Plus I have no clue how to get that older package amd 64 nvidia-current for precise, I searched high and low, seems odd it disappears so fast from the web but so many others hang around.

 I see why you do this, Ubuntu only gives you the 195 driver in nvidia-current for Lucid. I don't really have that issue. Maybe I should just use 2D which works but is not so fun and more ugly. I would not use the generic driver in 2D for any serious fun with photography which is what I like to do. But a fix may soon come down the pike from the repos.

Then I read your;

> After doing this, you **must** go by the following tutorial to install the driver into future kernels that are installed.
I'm also offline with this computer. It may be best to get the ubuntu version so new kernels don't mess me up? What if I just want to leave installed the first driver that works well. I may update the kernel because I get updates through the installation on my laptop which has Intel graphics drivers. I take the packages over to the offline nVIDIA desktop but the graphic driver version in use there will likely be frozen .... at least for longer periods of time because I won't think of it probably. Would the Ubuntu version nvidia-current driver be the best choice for that situation or would the manufactuerer driver be just as easy of a situation to maintain?

---

### Post by Mike_tn on 2012-04-25
Me again. You may not want to answer any of my questions above and I wouldn't blame you considering how verbose it is. 
(Mike_tn = -vvv)

Short Qs about your code on these steps:


**your step 6**
cd to the directory where you saved your file

Q: If the nVIDIA .run file is in HOME next to Documents, Downloads etc then is it true that I should not need to do any directory changes?


**your step 7**
Install drivers

    ```
sudo sh NVIDIA-Linux-x86_64-295.33.run
```I saw both that and the following on the nVIDIA site.

    ```
sudo sh ./NVIDIA-Linux-x86_64-295.33.run
```Do both of these work or no?


**your step 8**
Start GDM

```
sudo service gdm start
```Is that equal to this,

    ```
sudo /etc/init.d/gdm start
```

---

### Post by Cavsfan on 2012-04-26
> **Mike_tn said:**
> Do you get better results doing this manually? I'm running Precise for the first time, fresh Ubuntu install after being only on Debian Squeeze a long time so I have no Ubuntu packages in archives and the Ubuntu version of 295.40 nvidia-current will not install properly, maybe it's a bug in Unity, not sure. Easy fixes such as unity reset do not work.  My screen behavior seemed to match someone else who fixed it by installing the previous Ubuntu version of nvidia-current which uses 295.33 however I cannot find a download to that anywhere, I can only find the manufacturer version of that. Hence I read your post. Very detailed and easy to follow really. Makes perfect sense with everything I have read and tried in the last two days.  I'm only half-way a geek.  I would prefer to find the Ubuntu version of the driver but that could be a bad idea, you may have less bugginess cropping up doing it your way, I don't have enough experience to know. But it is also just plain fun to make computers work for you even if the advantage is only slight. Plus I have no clue how to get that older package amd 64 nvidia-current for precise, I searched high and low, seems odd it disappears so fast from the web but so many others hang around.

 I see why you do this, Ubuntu only gives you the 195 driver in nvidia-current for Lucid. I don't really have that issue. Maybe I should just use 2D which works but is not so fun and more ugly. I would not use the generic driver in 2D for any serious fun with photography which is what I like to do. But a fix may soon come down the pike from the repos.

Then I read your;

I'm also offline with this computer. It may be best to get the ubuntu version so new kernels don't mess me up? What if I just want to leave installed the first driver that works well. I may update the kernel because I get updates through the installation on my laptop which has Intel graphics drivers. I take the packages over to the offline nVIDIA desktop but the graphic driver version in use there will likely be frozen .... at least for longer periods of time because I won't think of it probably. Would the Ubuntu version nvidia-current driver be the best choice for that situation or would the manufacturer driver be just as easy of a situation to maintain?

If you went my these instructions, you will have to manually update the driver each time one comes available.
If you do not follow the instructions in the tutorial to install the driver into future kernels that are installed, you will have major problems I believe.
If the kernel is upgraded, it will be fine but, not when one is installed.
It is is a pretty simple tutorial.

---

### Post by Cavsfan on 2012-04-26
> **Mike_tn said:**
> Me again. You may not want to answer any of my questions above and I wouldn't blame you considering how verbose it is. 
(Mike_tn = -vvv)

Short Qs about your code on these steps:


**your step 6**
cd to the directory where you saved your file

Q: If the nVIDIA .run file is in HOME next to Documents, Downloads etc then is it true that I should not need to do any directory changes?


**your step 7**
Install drivers

    ```
sudo sh NVIDIA-Linux-x86_64-295.33.run
```I saw both that and the following on the nVIDIA site.

    ```
sudo sh ./NVIDIA-Linux-x86_64-295.33.run
```Do both of these work or no?


**your step 8**
Start GDM

```
sudo service gdm start
```Is that equal to this,

    ```
sudo /etc/init.d/gdm start
```

As long as you are in the directory where the installation file exists (enter **ls -l** to see what is in a directory).

    ```
sudo sh NVIDIA-Linux-x86_64-295.33.run
```has always worked for me. My files go to the Downloads directory, so I just have to enter **cd Downloads**.
[COLOR=Red](295.40 is what is currently available from the nVidia site.)[/COLOR]

```
sudo service gdm start
```is what I have always used in the past.

---

### Post by Mike_tn on 2012-04-26
Thanks for the replies Cavsfan;

**I tried to install. Two preliminary notes. **

-I left "nvidia-common" installed because the terminal wanted to remove "ubuntu-desktop" along with it.

-typing "login" at runlevel 3 did not work. I had to Alt+Backspace+F2
then login using my terminal prompt name and password.


**After that I tried it several ways, **

-An attempt immediately at the root shell prompt after clicking the recovery menu.

-Attempts using init 3,  telinit 3, and init 1.

-Tried with the word "root" in the prompt and with "mike" in the prompt.

-Tried with and without sudo

-Tried with and without ./ ahead of <filename> (after sh)

-Finally tried placing the NVIDIA...run file in Home directory and also tried it on root at /usr/local/mydebs and then cd to it.

-Also I tired various combinations of all of the above.
[B]
2 Results[/B]

-If I did not jump to a runlevel after the recovery menu then it could not open anything whatsoever.   

-If I did jump to a runlevel 3 or 1 in order to cut out X more fully then it said this:

```
mkdir: cannot create directory '/tmp/selfgz1327': Read-only file system
Unable to create the target directory...
```**Final try**

-I created a tmp folder of the name "selfgz1327" and put the NVIDIA....run file in there but it just said it could not make a tmp directory and picked a different name for it, changing the numbers in the name. It gave the same Read-only file system error.

Ideas?

Could nvidia-common being still installed have caused directory-creation and Read-only issue? I'm guessing it would not cause that.

P.S. This is using Precise Final Beta so it could have a bug. One wierd thing I noticed. When I went into a root folder and tried to copy-paste the NVIDIA...run file from /usr/local/mydebs to the tmp folder I made, the copy function looked normal but the paste function was greyed out however the paste still worked as if it the context menu lettering for the word "paste" was black. bugs I assume.

P.P.S. I did have root access because trying to restart gdm or reboot required root privilege and that worked.

---

### Post by Cavsfan on 2012-04-26
Not sure what to tell you. I do not have nvidia-common on my system. I checked via SPM.
When you drop to root shell (terminal) and enter **telinit 3** did you wait a few minutes to allow it to do it's thing?
Then when the prompt comes back I enter login and it asks for my username/password and I am in.
Then I go to where my driver is and make sure I am in the directory by entering **ls -l** and see it listed.
Then I enter ```
sudo sh NVIDIA-Linux-x86_64-295.40.run
```exactly as it is named. The capitals matter. If I get anything wrong it gets an error and I have to compare the file name with my command.
If it is wrong I use the up arrow key to display the command and change it. Then it works.
I did that with this latest version. 

The reason I mention enter **telinit 3** is that I have skipped that step and the installation said to quit and enter **telinit 3** and then install.
I tried to login first and then enter telinit 3 (which I believe stops the x server) and it went crazy. I had to reboot.
Entering **telinit 3** before logging in worked great for me.

I was able to install the latest driver and boot back up in less than 15 minutes. 
But, I have done it a few times and am comfortable with it plus I am on 10.04 probably the most stable version there is.

I have heard that 12.04 has issues with some nVidea cards, which is why I am not jumping into it yet.
I will wait until 12.04.1 comes out as by then the bugs have been pretty much taken care of.
I used to jump to the next version, but my HP printer/scanner/copier would not work so I went back to 10.04 LTS.

All I am doing is providing the links to do the work. I am not really providing the commands myself.
But, I can acknowledge that it does work as I have done it about 7-10 times. My windows 7 system tells me when a new driver 
comes out and asks me if I want to install it. Then I start checking manually for the Linux version as it comes out soon afterward usually.

If you do not have a whole lot invested in 12.04 or if you can backup your important stuff I would suggest a clean install of the new release.
Or 10.04 if you want to be safe until 12.04.1 comes out on July 19th.

If doing this the manual way is too much, there is also a deb you can add to get nVidia driver updates automatically:

[[COLOR=blue]_https://launchpad.net/~ubuntu-x-swat/+archive/x-updates_[/COLOR]]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

There is a tab "Any Series" that will take you to which version of Ubuntu you have.

---

### Post by Mike_tn on 2012-04-26
Cavsfan

Nice you were online and able to reply so fast.  I will be away from my Precise PC for the day so I will try again tonight and let you know tomorrow.

> **Cavsfan said:**
> When you drop to root shell (terminal) and enter **telinit 3** did you wait a few minutes to allow it to do it's thing?I did not wait real long after entering telinit 3, nothing like 1 minute. It did give me the prompt. Next time I will let it sit 120 seconds...get some tea. By the way, I thought it was cool to be in a shell and hit the arrow up to see all the terminal commands I had used while fully logged in. It was like I was in my installed gnome terminal. Very cool. First time I did that.

> Then I go to where my driver is and make sure I am in the directory by entering **ls -l** and see it listed.I will add this as a double check. Like light in a root shell. It's dark in there.

> The capitals matter. If I get anything wrong it gets an error and I have to compare the file name with my command.I'm sure the title of the file was correct, CAPS and all. I typed and printed out the instructions as you suggested, and they were modified for my specific procedures.

> If you do not have a whole lot invested in 12.04 or if you can backup  your important stuff I would suggest a clean install of the new release. Or 10.04 if you want to be safe until 12.04.1 comes out on July 19th. WOW just released in full. I hadn't seen that, must be released just today. Niiiice. Will do. The July due date on version 12.04.1 is a long way off. I will try a little more before waiting.

> All I am doing is providing the links to do the work. I am not really providing the commands myself.Correct. I did open both of the main links you provided and saved those and made a combo summary of them with your page and printed that. You are probably also saying you cannot answer a lot of the more technical questions I may run into but it works and are offering your own trial and error results. I find endorsements like your post to be VERY important. I haven't gotten deeply into the auto-updater portion yet. That part seems straight forward if and when I get that far.

> there is also a deb you can add to get nVidia driver updates automatically;[COLOR=Black] https ://launchpad.net[/COLOR]I avoid all PPA installations.

I *duckduckgo* searched the "**mkdir cannot create directory read-only**" output and found some more to try. You covered it a bit though when you suggested a fresh install. People said that message may pop up if there are any errors on my partition. fstab says"errors=remount-ro" ro for read only. So they suggest running fsck on the **unmounted** partition first to fix errors. Another linux person said to look at the /var/log/messages for logging on the problem. Not sure if Ubunutu has that file but I will look.

So I will do the fsck and/or reinstall the new release if needed.

I appreciate all the tips and can't wait to download the new 12.04 woo hoo!

---

### Post by Mike_tn on 2012-04-27
Cavsfan

Problem over.  I'm using the Ubuntu grade nvidia-current-295.40-0ubuntu1 driver in 2D mode. I'm happy with that until a fix comes down from the repos.

I worked on the read-only shell prompt problem several more hours to no success.  Not 100% sure why yet but I noticed my Windows clock on another partition was off by 3 days HA! Probably due to the installation. However, I noticed fsck would clean up some sort of time issue before I tried the shell commands so that likely was not the problem. Probably this: there were some shell text outputs when I worked, referring to a location  /usr/lib/update-notifier and then Read-Only mentioned. Later on when using the OS normally there were Error Dialogue boxes popping up referring to the same saying INTERNAL ERROR at /usr/lib/update-notifier/apt_check.py So I assume that's it, a bug.  

When I began this attempt I hadn't realised the nvidia-current-295.40-0ubuntu1 driver ran 2D mode. I assumed 2D Unity only used the driver you see when in a Live CD and have to choose "nomodeset" at boot time because of your nVIDIAs.  It's much better than that. More like the graphical quality in Lucid Lynx or Debian Squeeze with the proper driver applied. And my use in graphics is 2D, still photo images and text.  Happy ending.

Thanks for reading and taking the time to help.

---

### Post by Cavsfan on 2012-04-28
You are welcome. Glad you got it working again. I have heard there are problems with some nVidia cards in 12.04.
I am still on 10.04 and don't plan on upgrading at least until 12.04.1 comes out.

Lucid will be supported until April 2013.

About all I know is this method has worked for me a few times, so I can verify that at least on 10.04 Lucid Lynx it works OK.

---

### Post by Cavsfan on 2012-05-05
I just installed driver 295.49 and updated my kernels also. The new driver came out on May 3rd.

---

### Post by Cavsfan on 2012-05-06
These instructions have been proven to help 2 people running 12.04 Precise Pangolin successfully.

---

### Post by JKyleOKC on 2012-05-06
Just FYI: The discussion about "telinit 3" is actually a holdover from someone who originally used a RedHat-based distribution. For RedHat, runlevel 5 is GUI mode and runlevel 3 is CLI mode, and "telinit 3" forces the system into CLI mode with no need to reboot.

However, for *buntu and all other Debian-based systems of which I'm aware, runlevels 2 through 5 are all identical unless you explicitly modify the startup coding, and the normal runlevel is 2. Thus the "telinit 3" command does nothing, effectively.

As I said, this is just FYI. It doesn't hurt anything to do it. But it's not necessary, either.

---

### Post by Cavsfan on 2012-05-06
> **JKyleOKC said:**
> Just FYI: The discussion about "telinit 3" is actually a holdover from someone who originally used a RedHat-based distribution. For RedHat, runlevel 5 is GUI mode and runlevel 3 is CLI mode, and "telinit 3" forces the system into CLI mode with no need to reboot.

However, for *buntu and all other Debian-based systems of which I'm aware, runlevels 2 through 5 are all identical unless you explicitly modify the startup coding, and the normal runlevel is 2. Thus the "telinit 3" command does nothing, effectively.

As I said, this is just FYI. It doesn't hurt anything to do it. But it's not necessary, either.

It is necessary if you have installed the driver this way before. 
If you have used this method before, you reboot into recovery and drop to a root shell.
That is where you want to enter **telinit 3** and give it several seconds to display 5-7 lines before logging in.
If you do not do this, the nvidia driver installation will tell you to exit installation and enter **telinit 3** and then install the driver.
So, I got the command from experience. The first time you do it and remove your nvidia driver via **sudo apt-get --purge remove nvidia-*** 
you will not need to enter **telinit 3** because there is no driver installed.
Once you have installed the driver in this manner, there is no way to remove the old driver and (according to the installer) you must enter **telinit 3**. 
The new driver will then remove the old one before installing the new one.

---

### Post by JKyleOKC on 2012-05-06
Very interesting! This indicates that the fine folk at Nvidia are tailoring their driver installation/removal procedures to the RedHat standard configuration and ignoring the Debian community standards.

Let's hope that the keepers of our repositories quickly get the newer Nvidia drivers in place so that we don't have to go through these maneuvers! Fortunately both my systems with Nvidia video work properly with the 173 driver so I can live with DKMS automatically installing it whenever there's a kernel update...

---

### Post by Cavsfan on 2012-05-07
> **JKyleOKC said:**
> Very interesting! This indicates that the fine folk at Nvidia are tailoring their driver installation/removal procedures to the RedHat standard configuration and ignoring the Debian community standards.

Let's hope that the keepers of our repositories quickly get the newer Nvidia drivers in place so that we don't have to go through these maneuvers! Fortunately both my systems with Nvidia video work properly with the 173 driver so I can live with DKMS automatically installing it whenever there's a kernel update...

All I know is what I have experienced myself. 

You did notice the HOWTO: Automatically update manually installed NVidia drivers after kernel updates right?
It works very well at installing the driver into the newly installed kernel.

Myself, I like to use the most current (stable) driver nVidia has to offer. My driver is 295.49 dated May 3, 2012. 
I will install the next version as soon as I notice there is one.

My windows 7 system alerts me to a new nVidia driver and asks me if I want to download it. That is when I start looking for a new Linux driver.

---

### Post by Cavsfan on 2012-05-17
If any one is interested the latest nVidia driver came out for Linux yesterday 2012.05.16 version 295.53.

---

### Post by Cavsfan on 2012-06-11
I just installed nVidia driver 295.59 on lucid. I have a partition with Precise 12.04 playing around with it to become familiar.
I don't think I would attempt to update the driver on 12.04 at least with these instructions.

But, if anyone is still on Lucid and wants to update, the driver just came out today June 11, 2012.
This is not for the timid. Read the first post carefully.

---

### Post by firekage on 2012-06-18
Sorry for writing here - could You write, explain how to install new nvidia drivers, how to remove and blacklist nouveau, and how to restore nouveau and xorg drivers for 11.10?

---

### Post by Cavsfan on 2012-06-19
> **firekage said:**
> Sorry for writing here - could You write, explain how to install new nvidia drivers, how to remove and blacklist nouveau, and how to restore nouveau and xorg drivers for 11.10?

Those instructions are contained in the 2nd link of post #1. It is simply a matter of copying and pasting 
except for the driver version name. Which you will have to modify.

If you're not comfortable doing the commands, I would not even do this. Because if you do not follow them exactly as stated 
on the web pages you will have a system that does not boot. If you install the driver in this manner, you must perform the steps 
in the 3rd link to make the script and move the driver or else when a kernel gets installed in the future, the driver will not be 
loaded into the kernel and that kernel will not boot.

I am just supplying the 3 links. I have not performed this on 11.10 myself.

You might be better off using the xswat ppa which will keep your nvidea driver up to date.
Although I am unaware of how it will work on 11.10 here are the commands:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

```Then reboot after wards. That is probably the safest way to keep your driver up to date,

---

### Post by Cavsfan on 2013-01-18
I forgot how fun and easy it is to update the Nvidia driver in Lucid.
I just updated to version 310.19 and updated the script in /usr/src/.

Awww, I'm going to miss Lucid come April... :D

In all the newer Ubuntu versions using Lightdm it has been impossible for me to update the driver.
But, I did see on Quantal the other day when I installed a gnome-shell it pulled in gdm and asked me which one I wanted to control video.
Lightdm or gdm. I clicked gdm so, maybe I can do that there now. 

Aw what fun. :D

---

