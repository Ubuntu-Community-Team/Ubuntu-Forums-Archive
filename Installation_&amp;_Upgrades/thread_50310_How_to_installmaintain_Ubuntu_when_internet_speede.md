---
title: "How to install/maintain Ubuntu when internet speed/expertise is an issue?"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by byen on 2005-07-19
OK. First of all thank you for all those guys who helped me out while I had all those troubled moments while installing and using Ubuntu during those initial days of ignorance..... anways... I guess its time I did my share to spread the love....

Ok. After I first installed and fired-up my Ubuntu box...I was really impressed with how easy it was and how hasle free this Distro is... SO during my summer visit I decided tht I would install Ubuntu on my Uncle's computer (which by the way had Win ME and gets bug infested and unusable every coupla months)... so when his PC-complain calls dropped from one/week to 0 in 2 months... I figured it all went well... and was glad to find out that it sure did... But little did I know that all he had been doing in the last 2 months is show off his pc to his poker buddies and rave about how it hasnt crashed and all.... So this time when I went there, I had about 3 of his buddies asking me to help them out as they really seemed to like what I did to my Uncle's PC and how they were tired of Viruses and adware and asked me if linux was easy enough for them to use and that they would not mind trying it out.  ANd here comes the question....
ALl of them can be classified as Absolute newbies with no patience and zero knowledge! They only use their PCs for paying bills and browsing the web ...so, as far as I know...once I set up the box they should  be up and running for a while without any problems.... but my question is  Ubuntu - Hoary isnt up-to-date, out of the box and there are many applications that I would need to install on their pcs which would make things much easier. Applications such as firestarter, gkrellm etc.and since they all have slow/lame dialup connections,is there anyway I can download all these applications on my PC (here using broadband) and then install them on their pc's using a CD?? how can I help them keep their boxes up to date?
Please note. These guys are total newbies and Im their only tech-doorway to the world so if something has to be done..it has to be done by me! So...how do I start of ? where do i begin?
Thank  you for your time and effort. Hope you help me help these guys out!!

---

### Post by delltony on 2005-07-19
[QUOTE=byen]OK. First of all thank you for all those guys who helped me out while I had all those troubled moments while installing and using Ubuntu during those initial days of ignorance..... anways... I guess its time I did my share to spread the love....

Ok. After I first installed and fired-up my Ubuntu box...I was really impressed with how easy it was and how hasle free this Distro is... SO during my summer visit I decided tht I would install Ubuntu on my Uncle's computer (which by the way had Win ME and gets bug infested and unusable every coupla months)... so when his PC-complain calls dropped from one/week to 0 in 2 months... I figured it all went well... and was glad to find out that it sure did... But little did I know that all he had been doing in the last 2 months is show off his pc to his poker buddies and rave about how it hasnt crashed and all.... So this time when I went there, I had about 3 of his buddies asking me to help them out as they really seemed to like what I did to my Uncle's PC and how they were tired of Viruses and adware and asked me if linux was easy enough for them to use and that they would not mind trying it out.  ANd here comes the question....
ALl of them can be classified as Absolute newbies with no patience and zero knowledge! They only use their PCs for paying bills and browsing the web ...so, as far as I know...once I set up the box they should  be up and running for a while without any problems.... but my question is  Ubuntu - Hoary isnt up-to-date, out of the box and there are many applications that I would need to install on their pcs which would make things much easier. Applications such as firestarter, gkrellm etc.and since they all have slow/lame dialup connections,is there anyway I can download all these applications on my PC (here using broadband) and then install them on their pc's using a CD?? how can I help them keep their boxes up to date?
Please note. These guys are total newbies and Im their only tech-doorway to the world so if something has to be done..it has to be done by me! So...how do I start of ? where do i begin?
Thank  you for your time and effort. Hope you help me help these guys out!![/QUOTE]

1) Install apt-zip
2) follow the following steps
First, in /etc/fstab add the line(assuming that we have USB flash disk on /dev/sda)

/dev/sda1 /mnt/usbkey vfat user,noauto 0 0

Later in /etc/apt/apt-zip.conf configure the following lines

# MEDIUM should be defined in /etc/fstab with option `noauto'.

MEDIUM=/mnt/usbkey

# DEFAULT_APTGETACTION is the action taken by apt-get when neither

# the --aptgetaction nor the --packages options are given.

# Possible actions include: dselect-upgrade(default), upgrade and dist-upgrade

DEFAULT_APTGETACTION=dist-upgrade

Now refresh your repository

# apt-get update

Now put on USB flash disk list of needed packages:

# apt-zip-list

Of course, one can choose method other than dist-upgrade. For instance, i wanted to install gnucash. Then I had put on command line apt-zip-list --aptgetaction=upgrade --packages=gnucash.

One gets on USB flash disk to files:
- apt-zip.options which is conf file
- fetch-script-wget-<machine name> which is used for downloading

Now go with USB stick on some UNIX machine with high speed link, mount it and type
# sh fetch-script-wget-ico-notebook

Once the script had downloaded all needed packages, take the USB stick home, put it in USB port and write
# apt-zip-inst

---

### Post by WildTangent on 2005-07-20
ok...that made no sense to me...and i dont think itll make any sense to byen either. i too have been wondering how to put packages from the repos on a portable medium for updating machines with limited, or no connection.

-Wild

---

### Post by lotusleaf on 2005-07-20
["Off-line custom repository"](http://www.ubuntuforums.org/showthread.php?t=7455)

["How to Create Local Repository on Hard Disk"](http://www.ubuntuforums.org/showthread.php?t=20217)

^^^^^^ Do these help? :)

---

### Post by byen on 2005-07-20
[QUOTE=lotusleaf]["Off-line custom repository"](http://www.ubuntuforums.org/showthread.php?t=7455)

["How to Create Local Repository on Hard Disk"](http://www.ubuntuforums.org/showthread.php?t=20217)

^^^^^^ Do these help? :)[/QUOTE]
 havnt tried em yet...but will today and see if this works...i dont have a USB but have a CD...so lemme see... and thanks for the thread link lotusleaf....looks like i might find something there...
will keep you guys posted..... thank you for the replies.

---

### Post by delltony on 2005-07-20
[QUOTE=WildTangent]ok...that made no sense to me...and i dont think itll make any sense to byen either. i too have been wondering how to put packages from the repos on a portable medium for updating machines with limited, or no connection.

-Wild[/QUOTE]

It is really hard to help someone that doesn't give the specifics of what they do not understand. In terms of the USB that was only given as an example. Otherwise you store all the files locally on the fast computer they download to the working dir. Then you can simply use your favorite linux burning program to burn the data to the disk. If the data is too big tar ball it then run the split command on it to span it out.  Anyway was just trying to help.  ](*,)

---

### Post by WildTangent on 2005-07-20
[QUOTE=delltony]Of course, one can choose method other than dist-upgrade. For instance, i wanted to install gnucash. Then I had put on command line apt-zip-list --aptgetaction=upgrade --packages=gnucash.

One gets on USB flash disk to files:
- apt-zip.options which is conf file
- fetch-script-wget-<machine name> which is used for downloading

Now go with USB stick on some UNIX machine with high speed link, mount it and type
# sh fetch-script-wget-ico-notebook

Once the script had downloaded all needed packages, take the USB stick home, put it in USB port and write
# apt-zip-inst[/QUOTE]
this is where you lost me

-Wild

---

### Post by jiyuu0 on 2005-07-20
Have you tried this?

Unofficial Ubuntu 5.04 Add-On CD
[http://www.ubuntuforums.org/showpost.php?p=150088&postcount=1](http://www.ubuntuforums.org/showpost.php?p=150088&postcount=1)

---

### Post by lotusleaf on 2005-07-22
[QUOTE=byen]havnt tried em yet...but will today and see if this works...i dont have a USB but have a CD...so lemme see... and thanks for the thread link lotusleaf....looks like i might find something there...
will keep you guys posted..... thank you for the replies.[/QUOTE]

You're most welcome and here's another which I find quite cool:

["**HOWTO:  Custom repo (local or remote)"](http://www.ubuntuforums.org/showthread.php?t=42862)**

---

