---
title: "upgrade problems  ubuntu 14.04  to  ubuntu 15.10 blank screen"
date: 2016-05-26
forum: Installation &amp; Upgrades
---

### Post by Calum_Mackenzie on 2016-05-26
Today I saw that 15.10 was avaliable as an upgrade from 14.04 to  15.10 started the download all was going well (or so I thought) had to go out and when I returned I was greeted by a black blank screen! Now it appears I have lost everything! The Laptop is a Thinkpad-X61s I can access  the bios when starting up, but restore doesn't work. After some searching I saw a post about an older system on a different  pc having the same issue & it was suggesting trying Ctrl-Alt-F4 as a method of getting into the  command prompt. This does work,but, I get the message on screen; Ubuntu 15.10 user-Thinkpad-X61s tty4 Then in a line directly below;  user-Thinkpad-X61s login  I pressed enter & a line appeared  below Password    I have entered what was my password but it is not accepted!  Now I am completely  stuck wishing I hadn't started the upgrade!  Can anyone offer any advice - please.

---

### Post by Bashing-om on 2016-05-26
Calum_Mackenzie; Ouch : But, Welcome to the forum.

Let's see what we can do . Welcome to the terminal, as it is the more expedient method to communicate.

1st off in this, a learning experience in 'buntu, release 14.04 is a Long Term Support (LTS) release and the upgrade path is generally to the next LTS release. In this case that is 16.04. However, that automatic release upgrade will not be available until 16.04 is deemed as ironed out with the release of the 1st point release, scheduled for July 21.

That said, let us try and address your present situation. As a first guess as to what is going on ( not ) .. A proprietary graphic's driver in use in 14.04 that in the upgrade became broke in 15.10 ? Without a graphic's driver there will be no GUI.

So let's see what the graphic situation is.

Boot up the install to the login screen. Here active a console interface with key combo ctl+alt+F1.
In this console log into the system with you "user name" at the login prompt, followed by the requested password you have. Be aware when the pass word is entered there will be NO response to the screen. Enter your password blindly and hit the enter key. Security measure !

At this point in the trouble shooting, considering a graphic's driver issue, what is the hardware and IS a driver loaded ?
As you are at a console, and typing the returns from commands would be a laborious effort, we resort to a pastebin site to relay the needed info. We have such a site and to access it you must install the tool.
In this console interface, execute:
```

sudo apt install pastebinit

```
'sudo' to elevate you privilege level to that of the administrator to perform a system function ( install software) . Your password will be required.

Now that the tool is installed and available, transfer the info to the pastebin:
```

sudo lshw -C display | pastebinit

```
will take a few moments for the system to hunt up the info, and then transfer to the pastebin; Patience .
The result will be a URL back in terminal. Pass that link back here to the thread and we can access that file and see what the graphic situation might be.
Depending on what is in that file, is what we do next.

It's a terminal thing, the terminal is your friend.
[INDENT][INDENT]once you have done it
[INDENT][INDENT][INDENT]ain't nothing to it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2016-05-26
> Then in a line directly below;  user-Thinkpad-X61s login  I pressed  enter & a line appeared  below Password    I have entered what was  my password but it is not accepted!

You first needed to enter your user name & then the password. By pressing Enter you failed to log in. And so the password would not work.

At the Grub boot menu try selecting Advanced options for Ubuntu and then selecting a recovery mode kernel. At the recovery menu select Resume. That may get you to a working desktop using a fall back open source video driver. Then go to Additional drivers and change video drivers.

What were you going to do if you had succeeded in logging in to the command line? What commands did you think that you would try? Ubuntu 15.10 reaches end of life July this year. So, I really do not see any point in upgrading 14.04 to 15.10 when we can go from 14.10 to 16.10 directly and the time to do it will about the time that 15.10 is reaching end of life. But you are not the first one to make this jump.

The 16.04 release notes say this

> 14.04 LTS to LTS upgrades will be enabled with the 16.04.1 LTS point release, in approximately 3 months time.

[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes)

At this point we do not know if the upgrade finished. It might have stalled waiting for some user input. So, it might be worth a try to go to the recovery menu and first select Network. That will establish a connection to the internet and put the file system in read/write mode and then select Root shell prompt. And run these commands

```
apt update
apt upgrade
apt full-upgrade
```

To exit the root shell prompt type exit and then select resume.

Regards.

---

### Post by frank18 on 2016-05-26
> **Calum_Mackenzie said:**
> Today I saw that 15.10 was avaliable as an upgrade from 14.04 to  15.10 started the download all was going well (or so I thought) had to go out and when I returned I was greeted by a black blank screen! Now it appears I have lost everything! The Laptop is a Thinkpad-X61s I can access  the bios when starting up, but restore doesn't work. After some searching I saw a post about an older system on a different  pc having the same issue & it was suggesting trying Ctrl-Alt-F4 as a method of getting into the  command prompt. This does work,but, I get the message on screen; Ubuntu 15.10 user-Thinkpad-X61s tty4 Then in a line directly below;  user-Thinkpad-X61s login  I pressed enter & a line appeared  below Password    I have entered what was my password but it is not accepted!  Now I am completely  stuck wishing I hadn't started the upgrade!  Can anyone offer any advice - please.


Man; first thing you should not do upgrade,do instead a clean install,i have to advise you that 1604 is not working right at this moment even if you do a clean install ,too messy on most machines. i tried 1510 with clean install at one time and must say it was the worst install i ever did of an OPS,i also tried 1604 not very  stable, what a piece of crap for a new LTS release,back on 1404 which runs like a clock,maybe in 6 months it will be polished,but i doubt,Ubuntu 1604 requires 2GRam, what i think it's a treason on the part of Ubuntu, since no old machine will run it right which is a shame,Ubuntu is taking the wrong path,trying to copy Win10,but Win 10 works great on my machine where i could not run 1604 right.

---

### Post by Bashing-om on 2016-05-26
@frank18 Nope,

That reply is pure FUD ( fear, uncertainty and doubt, usually evoked intentionally in order to put a competitor at a disadvantage).

There are literally thousands on thousands who have installed 16.04 and experience nothing other than bliss. Not to say there are not problems, or not to take away from the fact that you have a problem. 
In the event of a problem in 'buntu, we address the problem and fix it. That is the 'buntu way.

Open up a thread on a support forum, or file a bug report.

@ Calum_Mackenzie;
Heed our concerns to resolve your issues, proceed on your merry way.

[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-05-27
Good afternoon & many thanks for the assistance Bashing-om, I have followed the above & I now have an error message as follows;  E: dkpg was interuptted,  you must manually run 'sudo dkpg  --configure a' to correct the problem

---

### Post by Bashing-om on 2016-05-27
Calum_Mackenzie; Hey, hey ...

Making progress..

Now we do need to see these outputs - Between code tags -
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
so we get the full error advisory and in context.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending on those outputs is what we do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-05-27
[IMG]20160527_185305 [/IMG] Hi, Bashing-om,  I started with 'sudo apt update' and got a massive amount of response,so much I took a picture and have attached  it (hopefully ) When I try 'sudo apt upgrade'  I get the following response 'E: dkpg  was interrupted,  you must manually run  'sudo dkpg  --configure  -a' to correct the problem. Likewise the response is the same  for 'sudo apt -f install'

---

### Post by Bashing-om on 2016-05-27
Calum_Mackenziel Ouch ..

That "  massive amount of response " is what we need to see .

Please please provide the requested outputs as requested. Between code tags -
This maintains formatting and readability, and allows us to work with the text output./
provide:
```

sudo apt update
sudo apt upgrade
sudo apt -f install

```
outputs.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With out this information, we can not provide advise.

[INDENT]in the know
[INDENT][INDENT][INDENT]is nice to be
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-05-27
I am not sure if image of screen attached or not, so trying again.

---

### Post by Bashing-om on 2016-05-27
Calum_Mackenzie; No Kay;

Let's try this:
```

sudo apt update 2>&1 | nc termbin.com 9999
sudo apt upgrade 2>&1 | nc termbin.com 9999
sudo apt -f install 2>&1 | nc termbin.com 9999
cat -n /etc/apt/sources.list | nc termbin.com 9999
tail -v -n +1 /etc/apt/sources.list.d/* | nc termbin.com 9999

```
which transfers the outputs to a pastebin site, from there we can access the files in a textual manner.
The results of the commands are URLs back in terminal. Pass those links back here.

[INDENT][INDENT]let's see
[INDENT][INDENT][INDENT]then we know what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by LukeMorrison on 2016-05-27
> **Calum_Mackenzie said:**
> [IMG]20160527_185305 [/IMG] Hi, Bashing-om,  I started with 'sudo apt update' and got a massive amount of response,so much I took a picture and have attached  it (hopefully ) When I try 'sudo apt upgrade'  I get the following response 'E: dkpg  was interrupted,  you must manually run  'sudo dkpg  --configure  -a' to correct the problem. Likewise the response is the same  for 'sudo apt -f install'

If I might poke my nose in here and with all due respect to Bashing-om, it looks like even before any of the commands will run, we need to run ```
sudo dpkg --configure -a

```

Once this completes, we should be able to continue with the commands that Bashing-om provided.

---

### Post by Calum_Mackenzie on 2016-05-29
Hi all, the command [code]  sudo --configure -a [code] gives the following response [code] sudo: unrecognised option ' --configure ' [code]  then in 5 separate  lines of code the response continues  [code] usage: sudo -h | -K | -V [code] [code] usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-U user]  [command] [code] [code] usage: sudo -1 [AbEHknPS] [-r role] [-t type] [-C num] [-g group] [--h host] [-p prompt] [-u user] [VAR=value] [-i |-s] [<command>] [code] usage: sudo -e [-r role] [-t type] [-C num] -g group] [-h host] [-p prompt] [-u user] file ... [code]

---

### Post by BigMoose81 on 2016-05-29
I am running into the exact same issue after trying to upgrade to 15.10 (in order to get to 16.04) through the Ubuntu software updater.

After reading this thread, I decided to do the following and so far it appears to be updating, so I am hoping the other steps will work after it finishes:

1. logged in as indicated before
 2. changed directories 2 levels down by "cd .." twice
 3. Confirm you are in the right place but checking the directory your in "ls" if you see root as a path (don't try to access it cause it will say permission denied) then you can proceed with the below command.

 ```
sudo dpkg --configure -a
```

---

### Post by Bashing-om on 2016-05-29
BigMoose81; Hello - Welcome to the forum.

The same advise from post#11 applies . We have to know the status of the package manager and what sources we are presently working with.

Provide the requested outputs - in whatever means is convenient to you and we see what has to be done.

there is a basis
[INDENT][INDENT][INDENT]to all thought processes
[/INDENT][/INDENT][/INDENT]

---

### Post by BigMoose81 on 2016-05-29
Thanks for redpsonding Bashing-om, those commands you provided failed for me before I tried what I typed above. And since I started the steps above it was too late to go back for me (I dove off the edge before checking for sharks I guess you could say). I might have gotten lucky, as it does appear as if the steps I outlined above fixed my problem and now 15.10 is loading fine and I have all my settings, files, etc. from 14.04 still intact.

I am now going to brave it out and upgrade toe 16.04 directly. :)

---

### Post by Bashing-om on 2016-05-29
BigMoose81; Outstanding ...

Pleased it is working out; and you provide the steps to resolve.
let us know how the upgrade to 16.04 turns out.

[INDENT]'buntu
[INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT]

---

### Post by BigMoose81 on 2016-05-29
Just a status update, looks like 16.04 has upgraded and is now running normally, got a little error that I reported but otherwise seems to be okay.

I will have to flush it out later.

To the original poster, please let us know if this fixed your problem as well as it seems we ran into the same issue.

---

### Post by Calum_Mackenzie on 2016-05-30
Good morning all, I tried the advice BigMoose81 gave, initially things looked very promising, went through what looked liked the install process,but now the process has halted. I will post the ERROR MESSAGE; resolvconf: Error /run/resolvconf/interface either does not exist or is not a directory  
dpkg: error processing package resolvconf (--configure):  
subprocess installed post-installation script exit status 1  
Errors were encountered while processing: 
resolvconf

---

### Post by Bashing-om on 2016-05-30
Calum_Mackenzie; Well ...

That ain't good .

Learn now to use code tags :
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and copy/paste the outputs to preclude the transcription errors.

OK, no networking .. and the package manager advises to have a look at a particular file:
> 
 Error /run/resolvconf/interface either does not exist or is not a directory 


What have we to work with ? :
post back - between code tags - the outputs of terminal commands:
```

ls -al /run/resolvconf/interface 
ls -al /run/resolvconf/resolv.conf
ls -l /etc/resolv.conf

```

Maybe a broken symbolic link ?

can not update if we have no networking.

[INDENT][INDENT]build it and they will come
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-05-30
The first suggested code gets this response [code]ls -al /run/resolvconf/interface: No such file or directory[code]
The second suggested code gets this response [code]ls -al /run/resolv.conf: No such file or directory[code]
The third suggested code gets this response [code]lrwxrwxrwx 1 root root 29 Nov 23  2015 [COLOR=#ff0000]/etc/resolv.conf [/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]-> [COLOR=#ff0000]../run/resolvconf/resolv.conf[/COLOR][code]

Please note the use of the red colour for some parts of the third response is directly copied from that which appears on my screen

---

### Post by Bashing-om on 2016-05-30
Calum_Mackenzie; WQell .. 


Ouch, the file " /run/resolvconf/interface " I expect to exist/
As per my output:
> 
sysop@1404mini:~$ ls -al /run/resolvconf/interface
total 4
drwxr-xr-x 2 root root  60 May 30 12:40 .
drwxr-xr-x 3 root root 100 May 30 12:40 ..
-rw-r--r-- 1 root root  23 May 30 12:40 eth1.dhclient

where in my case 'eth1' is my current interface .

My typo ! should be :
```

ls -al /run/resolvconf

```

let us make sure that the file that the symlink points to is present:
```

ls -al /run/resolvconf/resolv.conf

```

As an aside .. on  using code tags .. the termination is "[/code]" a slash preceding 'code' .
As to what we are going to do ..

[INDENT][INDENT]I do not know, yet .
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-05-31
Hi good morning all,
The response to suggestion 1 is; No such file or directory 
The response to suggestion 2 is below
"```
" ls cannot access /run/resolvconf/resolv.conf : No such file or directory  "
```"

---

### Post by Bashing-om on 2016-05-31
Calum_Mackenzie; Yuk ...

I honestly do not know what to make of the fact that the directory " /run/resolvconf " does not exist on your system.
No doubt we have to make it up .. and the proper contents of that directory . We venture now into territory that I have never ventured into before. What must we do to generate this directory ?

What Desktop Environment are you running: unity, KDE, gnome ???
We will assume that network-manager is required in this GUI, so what returns:
```

dpkg -l network-manager

```
Maybe re-install network-manager .. will be a real trick with no networking !

Do we have any network capability at all ?
what returns:
```

ping -c3 8.8.8.8

``` If we can ping we can wget, to acquire the files we need .

[INDENT][INDENT]this too
[INDENT][INDENT][INDENT]an adventure in learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-06-01
dkpg -l network manager; gets the response ```
No command 'dpkg' found, did you mean:
Command 'dpkg' from package 'dpkg' (main)
```

ping -c3 8.8.8.8; gets the response ```
connect: Network is unreachable 
```

---

### Post by Bashing-om on 2016-06-01
Calum_Mackenzie; Ouch ..

As we have no package management system ( dpkg ) and no networking . Let's just take the easy way out here and do a clean  fresh install . As dpkg is bad .. there is no telling on this system what else might be corrupt . I would never ever have full faith in this system from this time on. That is just my feeling; you may feel different. 

To rebuild this system starting with re-building 'dpkg' would be a real pain and a lot of time and effort on your part .
I say again, the better thing here is to take that nuclear option - save your personal data ... and do a RE-install.

However, It is your system, your time and your effort

[INDENT][INDENT]your call
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-06-03
Calum_Mackenzie;  Hey .....

Are we done here ? What is your decision ? Or, what did you do ?

[INDENT][INDENT]Keeping it clean behind us
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-06-06
Hi, good evening, before I take the proverbial nuclear option, I am giving the proverbial dice, one last throw - see link below, to another ubuntu support forum - which very nearly answered the problem, but for it appears we cannot get / force an internet connection to finally solve the issue - but still hoping :)

[https://answers.launchpad.net/ubuntu/+question/294824](https://answers.launchpad.net/ubuntu/+question/294824)

---

### Post by Bashing-om on 2016-06-06
Calum_Mackenzie; Hey hey ....

Good deal. I will stay tuned, see what the big boys come up with .

[INDENT][INDENT]I like
[INDENT][INDENT]no quit
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-06-08
Calum_Mackenzie; Well, well well ...

Wonder of wonders .. what updates will not do for us.

For advisement to others; from the bug report :
> 
15.10 now working, I immediately checked for updates & downloaded a lot of updates - restarted - and got an automated message from Ubuntu informing me that an upgrade was available to 16.04 - I started downloaded very nervously, expecting a crash again, but I can thankfully report 16.04 *installed no problem, even installing flash player as part of the update and everything now appears to be working as it should


Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)


[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

