---
title: "Start again fresh"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by Cilionelle on 2012-01-08
Hi there,

I'm back.  After a year plus time away, a friend returned an Ubuntu computer to me.  I'll be aiming to use it in church to put the song words up on a large screen via data projector, and perhaps use it as a supplementary computer in the house for my kids.  It's old, etc, but it works really well and I have fond memories of flailing my way through those early years of Ubuntu use... ah, the memories!  (Or should I say, "AGH!!!1!!one! the memories!")

Anyhoo, because my friend was using the beast as his primary laptop for ages and ages, it's got a lot of junk on it that I have no need of.  Is there a way to completely wipe the slate clean and start again, from within the OS?  It's currently running 11.04, and doing so fine.  I don't have any discs for it, neither do I have a large quota for downloading (I'm hijacking my friend's connection to type this...).

Thanks in advance for your help!

Cheers,
Cilionelle

---

### Post by raja.genupula on 2012-01-08
Hi 

Actually i am not getting issue properly but what i understand is you wanna install a fresh Ubuntu.

But you wanna keep the old one and wanna run both ?  or run a fresh one ?

---

### Post by Cilionelle on 2012-01-08
Thanks for the response, and sorry for the confusion.

> **raja.genupula said:**
> Actually i am not getting issue properly but what i understand is you wanna install a fresh Ubuntu.

But you wanna keep the old one and wanna run both ?  or run a fresh one ?
Nope.  Kill the old one, restart afresh.  But without downloading, sourcing, creating, building from the ground up or otherwise having an install disc.

I have only the computer that is in front of me.  Is there a way I can reinstall Ubuntu from within Ubuntu or the BIOS, etc?  Or from command line?

---

### Post by raja.genupula on 2012-01-08
If you have any Ubuntu ISO and a USB then your job will easier. do you ?

---

### Post by Cilionelle on 2012-01-08
> **raja.genupula said:**
> If you have any Ubuntu ISO and a USB then your job will easier. do you ?
Nope.  Nada!  :)

---

### Post by raja.genupula on 2012-01-08
then we have only one solution man .

open your software center and look the installed application . so keep what you wish to have and remove all other from there .

then run this

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update


this is what i know , all the best man.:):)

---

### Post by ajgreeny on 2012-01-08
You can do quite a lot to tidy up what you have got already, but you will need to be careful not to remove applications that you still want.

Firstly, decide which applications you _must_ have; a word processor, no doubt, but will abiword be good enough or do you want/need LibreOffice instead.  The same for a spreadsheet, gnumeric or LibreOffice.

Totem (movie-player) is the default for music and video, I think, but there are many other apps which you could use, and which may already be installed, but it is difficult to know in what way you need to use the machine.

So, in simple terms, you need to decide what you are going to do with the machine, and then remove any applications you see that are on it but you don't use or need, preferably using synaptic, which I think is much better and more flexible that the software-center.  Make sure those removals do not also remove any applications/utilities that you know you will need in the lists that will pop up when you hit the remove option on some applications.

If anything important does inadvertently disappear, you can get everything in the default ubuntu back again with the command line using ```
sudo apt-get install ubuntu-desktop
```There is no magic answer that I know of to remove junk, as you put it, but remember that linux is not like windows, where lots of unwanted applications can slow down a system.  Generally in linux, unneeded applications do nothing more than waste space on the hard disk.

The commands shown by raja.genupula
```
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get update
``` are certainly worth running after all the above as they will clean up the cache of downloaded packages, remove any unnecessary dependencies, and then make sure everything is up-to-date.

---

### Post by ottosykora on 2012-01-08
just to explain to you: 

if you for example mean command line interface, well this is just not the operating system, so from there I could install operating system....
no, this is not true, this is the full operating system running.

Any linux operating system has to be delivered somehow, either on some physical media like CD or flash stick or it has to be downloaded from the internet.
But for the download from internet, some running operating system with all the essential parts like drivers for the network adapter, for the rest of the hardware, and some programs to organize all downloads have to be present.

So either people use the same operating system to make it a newer version by connecting to internet, run the update and this will take some time and will fetch many parts, but far not all, from the repository server and replace it. This works mostly.

Other way to start from zero is to get the operating system on external media, but this can be ordered by normal mail also. Just go to the main site of ubuntu, and look there.

From there on you can install system completely fresh.
But also here , working internet connection during the install is nice, as then all special drivers and extra components can be installed the right way from beginning.

So if you want bypass long downloads, obtain the installation CD from ubuntu:

[http://www.ubuntu.com/download/ubuntu/cds](http://www.ubuntu.com/download/ubuntu/cds)

---

### Post by Cilionelle on 2012-01-08
Thanks, guys!  I really appreciate the help.

Follow-up question, then: His user-name and password (let's call it 'steve') are still front and centre.  I've added a second admin account and password ('reginald', but my gut tells me that probably there are some config files saved to his profile, or something that I'll miss.  Is there a way to get it to default to reginald@Laptop, rather than steve@Laptop?

---

### Post by ottosykora on 2012-01-08
> **Cilionelle said:**
> Thanks, guys!  I really appreciate the help.

Follow-up question, then: His user-name and password (let's call it 'steve') are still front and centre.  I've added a second admin account and password ('reginald', but my gut tells me that probably there are some config files saved to his profile, or something that I'll miss.  Is there a way to get it to default to reginald@Laptop, rather than steve@Laptop?

well such things will be stored in the /home/steve and would have permissions set to steve
you would need to move them to /home/reginald and set the permissions to reginald

do you have any specific configs or data in mind?

Mostly such operation is not needed.

---

### Post by Cilionelle on 2012-01-08
Nothing specific.  I just know I'd rather ask than assume...

---

### Post by Cilionelle on 2012-01-09
Okay, so having gone ahead and deleted my friend's user account, the computer won't boot the GUI.  I get three messages:

1) "Could not update ICEauthority file /home/steve/.ICEauthority"
2) "There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256"

Then it has the Ubuntu splash screen.  Following this:

3) "Nautilus could not create the following required folders: /home/glyclan/Desktop, /home/glyclan/.nautilus.

Once the <OK> button is pressed, I have a cursor and a blank desktop, just the wallpaper and no icons or menus.

So I guess I have a couple of questions: firstly, what do the messages above mean?  Secondly, how do I interrupt the boot process to log in rather to my own account ("reginald" let's call it)? Thirdly, how can I, once it is in the final stage, recover the menus and icons to work through some of the issues?  What are the keyboard shortcuts that I can use to get there?

Thanks again!

---

### Post by Cilionelle on 2012-01-09
As a point of interest, I can wait until the screensaver kicks in, and then log into reginald, but I can't log out of steve.

---

### Post by raja.genupula on 2012-01-10
I think your desktop was gone . open your terminal and then do 

sudo apt-get install --reinstall ubuntu-desktop

if in direct boot terminal not opening then do this thing by booting into recovery mode . It will be fine.

all the best .

---

### Post by ajgreeny on 2012-01-10
Was your machine set to autologin to user glyclan?

---

### Post by Cilionelle on 2012-01-10
Yeah, I guess it was.  Something I didn't check beforehand, it seems.  And 'glyclan' = 'steve' in my other examples.  It must've been one I missed...

Anyways, how do I turn off auto login?

Additionally, I still can't log out of steve because I can't get icons or menus.  Is there a keyboard shortcut to access the logout process, or the command line (which means I'd then need help with the logging out commands).

Thanks!

---

### Post by marinara on 2012-01-10
[http://buildall.wordpress.com/2011/05/24/how-to-disable-auto-login-in-ubuntu-11-04/](http://buildall.wordpress.com/2011/05/24/how-to-disable-auto-login-in-ubuntu-11-04/)
is how to disable auto-login

do you know how to get to a command prompt?

also I would suggest just downloading the ubuntu cd.  if your friend objects, just calculate the cost with a calculator.

---

### Post by Cilionelle on 2012-01-10
I don't know how to get a terminal up without the icons/menus, hence the request for a keyboard shortcut...

---

### Post by Cilionelle on 2012-01-11
Eventually downloaded 11.10 and installed that, so the thread is moot now.  Thanks all for your help!

---

### Post by varunendra on 2012-01-11
Hi,

Seems like I'm too late to jump in. I think I understand what your original goal was. What I don't understand is why nobody suggested you about [Remastersys]("http://www.geekconnection.org/remastersys/"). All you needed to do was to install it, run it and select '**distribution**' option to create a DVD iso which would have been a live installation DVD holding all the apps you had installed, but no user-specific settings or data. You could then use it to make a fresh install of the same OS+packages automatically, without the need to download anything, and without any previously stored passwords or settings.

(in contrast to this, the **backup** option also stores user-data and settings, password etc. which are retained on installations made from the iso)

Even though this thread is moot now, I'll suggest you to give it a try. I'm sure you'd like it as an amazing backup/distribution tool. You can add it to your repositories as told [here]("http://www.geekconnection.org/remastersys/ubuntu.html"), or can directly download its suitable packages from [here]("http://www.remastersys.com/repository/") to install it manually.

---

