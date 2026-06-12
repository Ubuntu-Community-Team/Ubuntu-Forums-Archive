---
title: "Different desktop for Unity"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by Tom6153 on 2013-01-29
I wanted to get rid of that anoying sidebar so i went to a site called ubuntu geek which recomended that i put this line into the command line
sudo apt-get install gnome-session-fallback
i did that
and then i switched off the computer and then switched it back on and now i have no desktop at all just a command line
please help

---

### Post by TheFu on 2013-01-29
Before installing anything, you want to make certain that the package DB is current. If it has been more than a few hours, I run:

**$ sudo apt-get update**

I'd run that first thing.
Next I'd run 
[B]
$ sudo apt-get install -f
[/B]
to see what was partially installed and hopefully that will complete the installation.If you logout, then you should see the new logon screen and should be able to pick which desktop environment you like by clicking the sprocket.  If this doesn't work, don't fear, just install another DE - like** xfce** or** lxde **or the entire desktop for either or both of those which I think is in the **xfce-desktop **or **lxde-desktop** packages.
BTW, I've read ubuntu-geek and think that you probably left off some critical commands or where trying them with a different version of Ubuntu than the instructions.
If you need to understand the commands, please, please use the man command.$ [B]man apt-get
[/B]will explain how apt-get works and provide tips for safe use.BTW, which version of Ubuntu are you running?

---

### Post by Tom6153 on 2013-01-30
I ran sudu get-apt update

and in the end it says that some index files failed to download. they have been ignored or old ones used instead.
a lot of lines are saying something wicked happened....

i will try the next command

---

### Post by Tom6153 on 2013-01-30
i ran the second command sudo apt-get install -f 
its says. reading package list ....done
building dependency tree
reading state information.....done
the following package was automatically installed and is no longer required
linux headers 3.5.0-17
0 upgraded o newly installed o to remove and 245 not upgraded

---

### Post by Tom6153 on 2013-01-30
i closed down the computer and reopened and i still have the command line so i guess like you said i will have to install something else
how do i do that?

i ran the man apt-get and it gave me an explanation so i guess man means manual

i am trying to run ubuntu 12.10 64 bit unity
i wanted to change to another desktop so i could get rid of the sidebar but i have just started to read the unity documentation and it explains how i can close the sidebar without going back to an earlier desktop
so now i really just need my desktop back

---

### Post by arpanaut on 2013-01-30
try:
```
sudo apt-get upgrade
```

to retrieve those 254 packages and install them.
this may help, post back with the results.

---

### Post by TheFu on 2013-01-31
> **Tom6153 said:**
> 0 upgraded o newly installed o to remove and 245 not upgraded

Well, you can't just install any package you want without issues if you haven't been patching your system.  I patch my machines weekly.  Ubuntu has reminders. You must have seen them.  If you aren't into that, let it automatically patch everything for you.

Every Saturday morning, I run these commands:
```
sudo apt-get update
sudo apt-get dist-upgrade

```
Assuming no errors, that is all you need to do to keep an Ubuntu system updated and all applications patched.  Of course, this only works while a specific version is under support, so for 12.04, that is until 2017-April.  I think 12.10 is only supported for a year, so 2013-Oct.

If there are issues, then you need to solve those before doing anything else.
When you are all up to date, the **dist-upgrade** command will return** 0 to be upgraded.**  

There is a difference between "upgrade" and "dist-upgrade". Almost everyone should use dist-upgrade by default. Only businesses and kernel developers might not want to.

After you get the 0 to be upgraded, we can answer how to install other desktops. BTW, these will all be "current", they are not old, just well-loved. ;)

Of course, most of these commands have GUI ways to accomplish them too, but GUIs are too hard to explain in a forum. Sorry. I don't use the GUI for this stuff anyway. It is so much easier to put those commands into a tiny script and run it on every machine - copy/paste is an amazing thing if you aren't into scripting.

---

### Post by Tom6153 on 2013-01-31
i brought a brand new laptop
wiped windows 8 off and installed ubuntu 64bit 12.10 unity, (latest)
then i wanted to swap the desktop for an earlier version
i did "sudo apt-get install gnome-session-fallback"
but then when i rebooted the machine it just opened to command line
so then i did sudo apt-get update 
and sudo apt-get install -f
but its not working
so then i just put ubuntu back onto the pendrive and plugged it in as i hoped the computer would just reboot from the pendrive again, but that also didnt work and all i get is a command line
i really dont know much about computers and i am really stuck
please help

---

### Post by ibjsb4 on 2013-01-31
I don't think that command works with 12.10, I think you must install gnome-shell to get gnome-classic in 12.10 or just switch back to 12o4.

---

### Post by Tom6153 on 2013-01-31
when i try sudo apt-get update i get error messages
its failing to fetch something......

---

### Post by Tom6153 on 2013-01-31
when i try sudo apt-get dist-upgrade it gives me a long list of all the packages that will be installed and then i say yes but then it says it cant verify any of the packages and if say yes anyway then i just get a long line of failed to fetch........

---

### Post by Tom6153 on 2013-01-31
ok i figured out that the wifi wasnt working, so plugged the computer in and reran sudo gep-apt update and sudo get-apt upgrade and it downloaded all the packages like you said however you said that if i run the command again then i will get 0 to upgrade but i ran the command again and its said
"0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded"
the following packages have been kept back
linux-image-generic

so i guess that means something is missing
not sure what you mean by gui methods, do you mean point and click with the mouse??
i open my computer and literally all i get is a black screen that asks me to give my login name and then password and then it just says.....
tom@tom-monza-t200:~$............ there is no mouse interface
i dont understand it because it seems to me that ubuntu is on the computer...... am i just missing some simple command to go to the desktop?
anyway, i really appreciate your help

---

### Post by Tom6153 on 2013-01-31
ok i reread your instruction and i ran sudo apt-get dist-upgrade and it said the missing package will be installed "linux image ect"  and it said 1 upgraded and 0 to be upgraded and then it said need to get 27.7mb of archives and i pressed yes.......
then it said err archive linux image
could not resolve security......failed to fetch........
so something is wrong

---

### Post by Tom6153 on 2013-01-31
the computer at the end of that recomended that i run sudo apt-get update so i did and now its saying error.....failed to fetch..........
some index files failed to download, they have been ignored, or old ones used instead

---

### Post by zvacet on 2013-01-31
```
sudo aptitude unhold
sudo aptitude safe-upgrade
```

---

### Post by howefield on 2013-01-31
Threads merged.

---

### Post by TheFu on 2013-01-31
> **Tom6153 said:**
> the computer at the end of that recomended that i run sudo apt-get update so i did and now its saying error.....failed to fetch..........
some index files failed to download, they have been ignored, or old ones used instead

tom, instead of describing the errors, please copy/paste them as text into your replies.  We are used to reading them.

apt-get vs aptitude .... meh. Both do about the same things. Aptitude is supposed to be a little smarter, but they both work on the APT package management DB, just like the GUI tool, synaptic does.  "Software Center" does too, but it seems to overly simplify the interface and actively limits which packages are shown to users.

If all that remains is the latest kernel update, we can move forward to getting a GUI running.

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xfce-desktop

```

Then reboot the machine. The xfce-desktop package will install a bunch of stuff.

You should see a GUI start up. If not, please find and post the relevant parts of /var/log/syslog and /var/log/messages - not the entire files, just those that have something do to with X/Windows starting.  Copy/paste please.

I'd also suggest that you reconsider running 12.10 and switch back to the LTS version - 12.04. Using the latest version means you will need to update operating systems in 3 months again, then again in October and again in April 2014.  With 12.04, a new OS install won't be needed for years.

---

### Post by Tom6153 on 2013-02-01
i think the wireless is not working on my new computer because it needs a new driver 
i am also uncertain if it is working or not when i plug it in because when i use the command sudo apt-get update i keep getting an error message and 'unable to fetch'

i dont know how to check to see if i am online from the command line

i think perhaps the best solution to this whole problem is simply to reload ubuntu from scratch from a usb stick
i have a stick with ubuntu 12.10 64bit on it however when i close the computer down and restart it it doesnt give me the option to boot from the stick

does anybody know the command line method of booting from the usb drive and reinstalling ubuntu, (i have no gui the computer opens in ubuntu but just gives me a command line.....)

please help

---

### Post by Tom6153 on 2013-02-01
ok didnt see your message because i didnt see the second page on the thread
i cant copy and paste the information because the gui isnt working
i am writing all of this on a second computer the first computer is my new laptop and i erased windows 8 and put ubuntu on and now i have no graphic interface no desktop no nothing it just boots up and gives me a command line....:(

anyhow, i will try the above commands.......

sudo apt-get update is working
sudo apt-get upgrade is giving me a new message today..... it says there are 3 things to be upgraded
i pressed yes
it did a lot of stuff without any error messages so it looks good
i will run sudo apt-get upgrade again to make sure that there are 0 remaining like you said
Ok! it says 0 upgraded and 0 0 0 so it looks good
i will run sudo apt-get install xfce-desktop
hmmmmm
it says unable to locate package xfce-desktop

hmmmmmmmmmmmm

well at least the internet connection is working now, slowly making progress..........

---

### Post by Tom6153 on 2013-02-01
It worked!!!!!!!
not sure how but i just rebooted and its working again
i guess that once all the packages were downloaded it just fixed itself
your help is much apreciated!!!!!!!!!

---

### Post by TheFu on 2013-02-01
To see if you are "online" try:
$ ping google.com

To capture the output from programs without a GUI, try:

$ name-of-program | tee /tmp/some-clever-name.log

To learn what the "tee" command does, try:
$ **man tee**

I shouldn't have recommended xfce, since I don't use it myself.  I prefer something lighter, but the GUI I use does not include many user-friendly extensions or applications by default.  It is LXDE.  To install is, try:

$ **sudo apt-get install lxde**

This should pull in any missing GUI packages necessary AND install a GUI login if the system isn't have one.  There might be an lxde-desktop package which includes many tools that average users like. I don't know.  I know what I want and it usually is not what the desktop package guys think we all need. ;)

By now, you know which 2 commands to run prior to installing any major package, correct? update followed by upgrade. Having a current system is important when installing new apps.  dist-upgrade every week.

For someone so new to Ubuntu, I'd strongly recommend using 12.04 as the base OS, then load the GUI(s) that you like.  Reloading the OS shouldn't take more than 20 minutes, right?

---

### Post by TheFu on 2013-02-01
> **Tom6153 said:**
> It worked!!!!!!!
not sure how but i just rebooted and its working again
i guess that once all the packages were downloaded it just fixed itself
your help is much apreciated!!!!!!!!!

About every week, please, please, please patch your system.

apt-get update
apt-get dist-upgrade

If you don't want to be bothered doing this, tell Ubuntu to do it automatically for you, but you need to leave it powered on enough to allow it time to do it in the background.

I'm glad that you got it working.

---

