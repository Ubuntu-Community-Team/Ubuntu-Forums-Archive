---
title: "Schedule Automatic Updates."
date: 2012-09-18
forum: Installation &amp; Upgrades
---

### Post by UAdnan on 2012-09-18
Greetings,


Here's my little scenario fellow 'buntuers, I have a Xubuntu Distro ( 12.04 ) as shown in the title, and _I would like to know if there's any possible mechanism or method to automate the process of downloading my updates _( those of the Update Notifier,obviously. ) .

The reason behind my request is that I prefer the updates to be **_downloaded _***( _downloaded, not installed_ )*  by their own, and at a specific time, which is more likely to be a fixed time, midnight. There isn't any fairy tale behind that, just the ISPs of my country that limit us to very low traffic caps *( I can only download and upload 10GB per month otherwise I will have to pay extra charge.),* while at midnight and until the early morning 7:00AM, it's free ( implying fair usage policy though. ).

So if there's any application / Script / Shell (?) or anything that could do this, highly appreciated is your help. 
I'm a computer savvy, it's my main interest, but don't take me as a full expert, not yet. So please make it clear, not noob-clear, but clear, or just don't be too obscure.

Thanks in Advance, hope that wasn't too much of useless talking.

UAdnan.

---

### Post by dino99 on 2012-09-18
i'm not usint xubuntu, but you should glance at the package manager settings, at least you should set it to daily (after midnight)

or you need to write a cron job for it.

---

### Post by UAdnan on 2012-09-18
> **dino99 said:**
> i'm not usint xubuntu, but you should glance at the package manager settings, at least you should set it to daily (after midnight)

or you need to write a cron job for it.

Hello, and thanks for your support.
But can you help me about something ? What's the program ( or however it must be called  ) that actually starts updating my stuff ? Because if I choose the update manager itself, I guess it will wait until I press "Update." , so is there another thing beneath pressing the button after I had automated the execution of the update manager ? It would have been a good thing if Cuttlefish had this.

I don't know if there's any else, but I have Synaptics Packages Manager, and there doesn't seem to be such thing you're talking about. But all I need to know here, is, what's the "program" that downloads the update ? Or is it just within the Update Manager ? In other words, letting the update manager start automatically is quite useless since I will have yet to press Download.

---

### Post by Deepak A on 2012-09-18
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Get update software list, enter:[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]apt-get update[/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Update software(s) i.e. apply updates:[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]apt-get upgrade[/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#010101]**If you wish to automate the same, you can set it as a CronJob. **[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#797979][FONT=Courier New]apt-get install Crontab*[/FONT][/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Do the following thing before adding the job,[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]First create a directory for your script. (This is optional),[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]mkdir -p /data/myscripts[/COLOR][/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#797979]cd /data/myscripts[/COLOR]
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]Open a file,[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]vi autoupdate.sh[/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Type in the following lines;[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]#########################[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]#!/bin/bash

echo Updating Software List....
apt-get update

echo Updating Softwares ....
apt-get upgrade -y[/COLOR][/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]
[/COLOR][/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]
echo Script Ends....[/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]#############################[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Add executable permission to the file just created.[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]
chmod +x autoupdate.sh[/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Now u need to add your direcory to the path variable,\[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]PATH=$PATH:/data/myscripts[/COLOR][/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Now Check the script is working or not by just typing "[/COLOR][FONT=Courier New][COLOR=#797979]autoupdate[/COLOR][/FONT][COLOR=#010101]". if the path is set it will work properly. Otherwise you need to try running [/COLOR][FONT=Courier New][COLOR=#797979]./autoupdate.sh[/COLOR][/FONT][COLOR=#010101] from /data/myscripts directory. [/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]
Open a crontab by,[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]
crontab -e[/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Add the following line to it,[/COLOR][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]00 01  *   *   *    /data/myscripts/autoupdate.sh[/COLOR][/FONT][/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]Restart the Cron service,[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]/etc/init.d/cron restart[/COLOR][/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma]Your script will run everyday at 1:00AM. You can change the time by reading the instruction from cron file, [/FONT][/COLOR][COLOR=#000000][FONT=Tahoma]the format is,[/FONT][/COLOR]

[COLOR=#000000][FONT=Tahoma]min        hour        dom(day of month)        mon        dow(day of week)          command
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Example: 28   14    *    *    *    /bin/date
[/COLOR][/FONT][/COLOR]
'*' is used for repeation. Also, its using 24 hour format. 

Hope it may help.... 

Deepak. A

---

### Post by UAdnan on 2012-09-18
> **Deepak A said:**
> [COLOR=#000000][FONT=Tahoma][COLOR=#010101]Get update software list, enter:[/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][FONT=Courier New][COLOR=#797979]apt-get update
[CENTER]**[...]**[/CENTER]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Tahoma][COLOR=#010101]Example: 28   14    *    *    *    /bin/date
[/COLOR][/FONT][/COLOR]
'*' is used for repeation. Also, its using 24 hour format. 

Hope it may help.... 

Deepak. A

Well, it might have helped if I didn't face the following issue :

the shell script written would only work when I execute it from within the terminal. But when I double click the file to execute it just doesn't appear, which I think is the reason why the schedule done in crontab isn't being done, nor is it running in background as no internet traffic is being used as is telling me the gnome system monitor. I don't know why is it refusing to start in a not-yet-existing terminal, aka starting it by itself.

[COLOR="Red"]**EDIT :**[/COLOR]
Well, after thinking about it and fixing some stuff, I have come to this :
the .sh file contains the following :

[I]#!/bin/bash
xterm -e sudo apt-get update && sudo apt-get upgrade --force-yes [/I]

If there's something wrong in it please tell me.

Well, the problem that's solved now is that I can execute the problem finally without the need of a terminal, and from now on I will be using Cuttlefish instead of Crontab, both are easy mechanisms but it feels that using that Cuttlefish program is more fail proof, am I wrong ?
Now when the xterm terminal opens up it asks me for my password, because of *sudo*, so is there anyway whether to automatically start xterm as root or to make it type the password by itself ? I have tried removing the sudo and just do things with no root privileges but I got back to my first problem.

---

### Post by Deepak A on 2012-09-19
> **UAdnan said:**
> Well, it might have helped if I didn't face the following issue :

the shell script written would only work when I execute it from within the terminal. But when I double click the file to execute it just doesn't appear, which I think is the reason why the schedule done in crontab isn't being done, nor is it running in background as no internet traffic is being used as is telling me the gnome system monitor. I don't know why is it refusing to start in a not-yet-existing terminal, aka starting it by itself.

[COLOR=Red]**EDIT :**[/COLOR]
Well, after thinking about it and fixing some stuff, I have come to this :
the .sh file contains the following :

[I]#!/bin/bash
xterm -e sudo apt-get update && sudo apt-get upgrade --force-yes [/I]

If there's something wrong in it please tell me.

Well, the problem that's solved now is that I can execute the problem finally without the need of a terminal, and from now on I will be using Cuttlefish instead of Crontab, both are easy mechanisms but it feels that using that Cuttlefish program is more fail proof, am I wrong ?
Now when the xterm terminal opens up it asks me for my password, because of *sudo*, so is there anyway whether to automatically start xterm as root or to make it type the password by itself ? I have tried removing the sudo and just do things with no root privileges but I got back to my first problem.


First of all CronJob is a background job. It will automatically run if the configurations are correct. For our Updating purpose  make this job as a Root's job. Create the script and set the cronjob as a root user. Once the job is executed a mail will be sent to the creator of the job. So check root's mail by simply typing "mail" from a terminal. Or if you want your job to run in your current terminal, You need to redirect the output to your current terminal.

For that Just type in "tty" from a terminal. 

#tty
/dev/pts/0

 the output will be something like this. Copy this information and edit your cronfile.

#crontab -e

####################################

# m  h  dom  mon  dow   command

  28  20   *      *      *      /data/myscripts/autoupdate.sh >> /dev/pts/0

####################################

restart the service.

#/etc/init.d/cron restart


I don't know much about cuttlefish, i am more familiar with Crontab. 

Deepak :)

---

### Post by UAdnan on 2012-09-19
Hi ! 

I've got my issue solved out, after hours of rant and ... Mhm.

Well I apologise that our attempts of doing it failed, instead I've found an alternative way, which is one simple thing to type in the crontab file :
[URL=http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/]
** * * * * (/usr/bin/aptitude -y update && /usr/bin/aptitude -y safe-upgrade) 2>&1 >> /var/log/auto_update.*[/URL]

And for my case it would be *00 00 * * * (/usr/bin/aptitude -y update && /usr/bin/aptitude -y safe-upgrade) 2>&1 >> /var/log/auto_update.*

Thank you for your support.

---

