---
title: "How to write a script to manage nightly downloading?!"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by SidebySide on 2011-08-11
Hi Free-Users!
This is my first topic, & my English isn't well. pardon me plz.
[COLOR=SeaGreen]---------------------------------------------------------------[/COLOR]
Downloading at night(02:00 Am - 07:00 Am) is free here(my zone), and it's the time that I'm at sleep!
I want to use a command text to run in startup at boot (into Console, which I prefer) or in start up of GUI when the OS (here Ubuntu) loads, in order to install many softwares as in stellarium, Octave, Samba, etc, which usually are heavy(high size in download) + downloading files.
AND I don't have much experiences in script writing in bash.
First I try to explain my intention and my discovered.
* I know there is some GUI softwares,but I prefer CLI & my real goal is installing softwares(at night, when ADSL is free)
**[COLOR=SeaGreen]_---------------------------------------------------------------_[/COLOR]**

[COLOR=Red]** [/COLOR]:-k[COLOR=Red] Problems[/COLOR]
[COLOR=DarkOrange]a[/COLOR]- sudo
which I should be behind my PC at 02:00 to enter my password for each software, It's hard to me, due to I should get up early!

[COLOR=Lime]b[/COLOR]- 2 unpleasant questions which emerge after running "apt-get" utility:
Do you want to continue (Y/n)? y
Install these packages without verification (y/N)? y

[COLOR=SlateGray]c[/COLOR]- Timer!
System should turn on at night, in specified time, and turn off in specified time, too, or when the process(download-install) is finished.

[COLOR=DeepSkyBlue]d[/COLOR]- re-trying
It is possible the connection cut off for a moment, breaking process to  fetch or something els may happen, so apt-get will cancel or jump to next line. The script should define that apt-get(or aptitude) stay in the line which not finished successfully, repeating to succeed.

[COLOR=Magenta]e[/COLOR]- log file
It's necessary to know what happened during night. script should save a log file to show result of processing.

[COLOR=Sienna]f[/COLOR]- Start-Up
runnig script at startup
**[COLOR=SeaGreen]_---------------------------------------------------------------_[/COLOR]**

** ;) Solutions
I've found these:

1. One sudo for several program:
```
apt-get install software1 software2 software3 ...
```2. Escape sudo!
**1st way:**
```
sudo gedit /etc/sudoers
```adding this line at the end:
```
%username ALL = (ALL) NOPASSWD: /app/you/want/to/run/as/sudo
```e. g.
```
%sidebyside ALL = (ALL) NOPASSWD: /usr/bin/eject
```then
```
sudo visudo -c 
```**2nd way:**
sudo ability for reading password from entry, this way:
```
echo 123456 |sudo -S apt-get install stellarium
```**3rd way:**
Writing a script for "pass" variant to read an new & unimportant created password. in order to this trick, it's essential to write another script to define an unreal password, then pour the password into a file, keep it for a short time (e.g. 5min), then clean it. Now it's just enough to introduce that file to sudo (using "pass" to read the unreal created password for sudo within that file), sudo will be defrauded and, we will pass it and at this time, the rest command is running.

3. passing 2 mentioned questions:
using "yes" command, this way:
```
yes y |sudo apt-get install stellarium
```3. Specifying time for turning on/off
Turn on the computer via BIOS: [Click Here]("http://askville.amazon.com/set-computer-boot-up-automatically/AnswerViewer.do?requestId=4933774")
Turn off the system via command line (using script)
```
sudo apt-get install timeout
```This way:
```
 timeout 5h sudo apt-get install stellarium
```... will finish the process, 5 hours after running the command (here apt-get)
using "shutdown 0" or another command like this in next line will be usefull: 1st state: if the Process won't succeed at specified time into "timeout" command, then system will shutdown after (here) 5 hours.
2nd state: The Process finish sooner than the specified time and then system will shutdown immediately.

4. Running the script in Start-Up
So you have a script of your own that you want to run at bootup, each time you boot up. This will tell you how to do that.
Write a script. put it in the [COLOR=Magenta]/etc/init.d[/COLOR] directory.
Lets say you called it FOO. You then run
[COLOR=SeaGreen]% update-rc.d FOO defaults[/COLOR]
You also have to make the file you created, FOO, executable, using
```
chmod +x FOO
```You can check out
[COLOR=SeaGreen]% man update-rc.d[/COLOR] for more information. It is a Debian utility to install scripts. The option “defaults” puts a link to start FOO in run levels 2, 3, 4 and 5. (and puts a link to stop FOO into 0, 1 and 6.)
Also, to know which runlevel you are in, use the runlevel command.


[FONT=Comic Sans MS][SIZE=2][B][COLOR=Purple]AND
I found this script for *[COLOR=Blue]Arch linux[/COLOR]*, so near to my goal[COLOR=DarkOrchid]:[/COLOR][/COLOR][/B][/SIZE][/FONT]
#(put these line into a raw file and put the file into /etc/rc.conf before emerging kdm, this script will download from 02:00:00 Am, when the computer turns on for 5 hours and run the link placed into /home/USERNAME/wgetlist in respectively, Continuing broken downloaded file or starting a new one. You can merge bellow script with "vbetool dpms off" to save energy by turning off monitor)
```
TZ='Asia/CAPITAL'; export TZ
h=`date +%k`
date
if [ $h = '2' ]
then 
echo "press any key to cancel dowload! (waiting 4 seconds!)"
read -t 4
if [ $? = '0' ]
then
exit
fi
cd /home/USERNAME/
echo "yes" > autohalt
timeout 5h wget -c -i /home/USERNAME/wgetlist
halt=`cat autohalt`
if [ $halt = "yes" ]
then 
halt
fi
fi
```[CENTER][COLOR=Red]___________________________________[/COLOR]
[FONT=Lucida Console]**[SIZE=3][COLOR=Red]_My Questions(demand)   _[/COLOR][/SIZE]**[/FONT]
:?:
[/CENTER]

[B][SIZE=2][U]More/better solutions to above problems?
How to leave a log file?
How to insist on apt-get to don't cancel the process before prosperity!
How to mix these to write a script for mentioned intention, above?
How to write this script?
[/U][/SIZE][/B] if you help me step-by-step, I'm thanks.

Thanks for spending time to read this long text, more for your answers(if!)

---

### Post by SidebySide on 2011-08-12
> **Major_Bloodnok said:**
> crontab
JDownloader

1. [COLOR=DarkOrchid]**My main aim: Installing software at night via apt-get or aptitude**[/COLOR]
[U]
2. JDownloader[/U] is a graphical one, far from my aim.
_CronTab_ Just can set time, but it's really useful. tnx.
no more idea?

---

### Post by SidebySide on 2011-08-23
any more data?
any experience?
The best solution for:
        [B][SIZE=2][U]More/better solutions to above problems?
[/U][/SIZE][/B]        [B][SIZE=2][U] How to leave a log file?
[/U][/SIZE][/B]        [B][SIZE=2][U] How to insist on apt-get to don't cancel the process before prosperity!
[/U][/SIZE][/B]        [B][SIZE=2][U] How to mix these to write a script for mentioned intention, above?
[/U][/SIZE][/B]        **[SIZE=2]_How to write this script?_[/SIZE]**

---

