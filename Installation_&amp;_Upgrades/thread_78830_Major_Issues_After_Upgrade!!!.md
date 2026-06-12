---
title: "Major Issues After Upgrade!!!"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by katiad on 2005-10-19
Major problems here. 

So I've been trying to upgrade, and continually got errors. Someone finally posted a solution - to remove the us from us.archives.ubuntu to get the upgrades to go through. Well, everything seemed to work all right, and then, shortly after the Dictionary asked me to input which default dictionary to use, Synaptic froze up. I rebooted the computer... and now... everything's wrong.

It claim's it's upgraded to Breezy, but I get these issues: upon startup, I get error messages (on another computer, so I may abbreviate a bit as I have to type them out after writing them down):

perl: warning: Settling locale failed.
perl: warning: Please check that your locale settings:
    Language = "en"
    LC_All = (unset)
    LANG = en_US.UTF-8
are supported and installed on your system.

More errors regarding the locale pop up in various places.

Then, X fails to start. Doing a dpkg-reconfigure xserver-xorg only produces more locale errors, and then ends in:
xserver-xorg is broken or not fully installed

I attempted, then, to install another program (burn) to hopefully copy my /homedirectory to cd (discovered that /home/ was not on a separate partition as I thought it was... grrr) and came up with some errors and advice to try an apt-get -f install - so I did. Well, that proceeded to attempt more of the upgrades that had failed... errors ended in:

/var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8.i386.deb
E: sub-process /usr/bin/dpkg returned error an code (1)

(a lot of the errors had to do with libofx2)

I also tried to reinstall my nvidia graphics drivers. Didn't work. 

Advice? Ideas? If I can find a way to safely copy my /home directory I'm more than willing to do a complete reinstall....  but of course, fixing this in another way would be more useful.

---

### Post by pinoyskull on 2005-10-19
my advise, reinstall, it's the safest way

---

### Post by pestie on 2005-10-19
I'd like to know more about those perl locale warnings, too. A Google search of the phrase "perl: warning: Settling locale failed" turns up absolutely nothing, which is very unusual ("Setting locale failed" also turns up nothing). But I'm getting a huge number of these errors in the Synaptic terminal window. Nothing seems to be breaking as a result, but there must be something missing, so if anyone can point me to the correct package to install, I'd greatly appreciate it.

---

### Post by katiad on 2005-10-19
Okay, so... got advice on how to backup my files? Need my thunderbird mail, firefox bookmarks, and a few files in my /home directory.

Tried cdroast. Can't do a scanbus... errors come up....

---

### Post by katiad on 2005-10-19
edit: make that cdrecord. I'm tired. Don't know what I'm typing.

---

### Post by frodon on 2005-10-19
Same error for me, arg ..... i don't want to reinstall all my softwares, does anyone here found a way to solve this problem ?

---

### Post by meriva on 2005-10-20
Hi all,

same problem for me with locale support (it).
I'm no more able to install locale(it) (synaptycs refuses to install it) but the system works (I was lucky).

I'll wait until a solution will be adopted just to be safe.

Sorry cannot help.

---

### Post by frodon on 2005-10-20
Problem solved for me, the install worked well despite the errors. Then after the reboot i installed the fr language package, and now all works perfectly !

---

### Post by leezer3 on 2005-10-20
Hiya,
The locale warnings are of no consequence at all, just a byproduct of a couple of changes in Breezy, and can be safely ignored.
For those of you haveing problems installing locales, do this through the Gnome locales manager, as opposed to apt-get and it should work. 
@katiad: My advice would be to boot with the livecd, and then backup your stuff from there before doing whatever.
I'm not quite sure why your X-Server doesn't wish to play ball- Maybe try & reinstall the package, and see if it works- The only X-Server problems I've come across on upgrades are those related to a bad xorg.conf, which yours clearly isnt.

Cheers

-Leezer-

---

### Post by standingfire on 2005-10-20
[QUOTE=katiad]Major problems here. 

So I've been trying to upgrade, and continually got errors. Someone finally posted a solution - to remove the us from us.archives.ubuntu to get the upgrades to go through. Well, everything seemed to work all right, and then, shortly after the Dictionary asked me to input which default dictionary to use, Synaptic froze up. I rebooted the computer... and now... everything's wrong.

It claim's it's upgraded to Breezy, but I get these issues: upon startup, I get error messages (on another computer, so I may abbreviate a bit as I have to type them out after writing them down):

perl: warning: Settling locale failed.
perl: warning: Please check that your locale settings:
    Language = "en"
    LC_All = (unset)
    LANG = en_US.UTF-8
are supported and installed on your system.

More errors regarding the locale pop up in various places.

Then, X fails to start. Doing a dpkg-reconfigure xserver-xorg only produces more locale errors, and then ends in:
xserver-xorg is broken or not fully installed

I attempted, then, to install another program (burn) to hopefully copy my /homedirectory to cd (discovered that /home/ was not on a separate partition as I thought it was... grrr) and came up with some errors and advice to try an apt-get -f install - so I did. Well, that proceeded to attempt more of the upgrades that had failed... errors ended in:

/var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8.i386.deb
E: sub-process /usr/bin/dpkg returned error an code (1)

(a lot of the errors had to do with libofx2)

I also tried to reinstall my nvidia graphics drivers. Didn't work. 

Advice? Ideas? If I can find a way to safely copy my /home directory I'm more than willing to do a complete reinstall....  but of course, fixing this in another way would be more useful.[/QUOTE]


Best thing that I can think of is to back out as much as possible of the Xserver installation, clear the cache files and reinstall a few pieces at a time.

---

### Post by Nachtengel on 2005-10-20
Exact Same Issues I'm having (though the dpkg errors are for libopenh).  Additionally Breezy didn't want to start my dhclient on boot (manually started myself upon discovery).

I'm fairly new to Linux, so when you say to back out of the Xorg install, what exactly, do you mean?  A link to some directions would be fantastic.

Also, some advice on recovering thunderbird mail would be fantastic.... guess I'd be safe copying the whole /home directory?

---

### Post by leezer3 on 2005-10-20
Hiya,
If you have a GUI, which it sounds like you do, then there is no point in uninstalling the XServer.
If you do have a GUI, first use the locales manager to update everything to the new Breezy locales, and then open a command. Run:
```
apt-get dist-upgrade
``` and hopefully this should clear up any remaining problems.

Cheers

-Leezer-

POST #100!!

---

### Post by meriva on 2005-10-21
[QUOTE=leezer3]Hiya,
If you have a GUI, which it sounds like you do, then there is no point in uninstalling the XServer.
If you do have a GUI, first use the locales manager to update everything to the new Breezy locales, and then open a command. Run:
```
apt-get dist-upgrade
``` and hopefully this should clear up any remaining problems.

Cheers

-Leezer-

POST #100!![/QUOTE]


A thought: I'm having some problems during these days by keeping my system up-to date, repository don't work, locale problems.
Should it depends on the new release or not?

Sorry but I'm new on Ubuntu, just more than 1,5 months.

Thanks

---

### Post by flower on 2005-10-21
man I had exactly the same issues with the same package and the locales ...
I tried to upgrade from cdrom trough synaptec - didn't succed.
I tried to upgrade by atp-cdrom, apt dist-upgrade - didn't succed.
I tried to upgrade via synaptic from the breezy repositories - didn't work also...

I tried to install from the cdrom - didn't work too ... 
My advice - wait a bit until the distro is a bit more stable.

How to backup your files ? Use Knoppix - I always have a cd with it for emergencies like this ;)

---

### Post by meriva on 2005-10-21
I've finally fixed the problem.
Even if locale gives simply warning messages, I felt like something was not going fine.
I've downloaded locales file from 

[http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb](http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb)

did: sudo dpkg -i locales_2.3.5-1ubuntu12_all.deb

last step: sudo dpkg-reconfigure locales

and now locale problems are fixed :razz:

Hope was useful.

Ciao

---

### Post by leezer3 on 2005-10-21
[QUOTE=meriva]I've finally fixed the problem.
Even if locale gives simply warning messages, I felt like something was not going fine.
I've downloaded locales file from 

[http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb](http://ftp.belnet.be/packages/ubuntu/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb)

did: sudo dpkg -i locales_2.3.5-1ubuntu12_all.deb

last step: sudo dpkg-reconfigure locales

and now locale problems are fixed :razz:

Hope was useful.

Ciao[/QUOTE]

Correct- By installing that .deb file, you installed the new Breezy standard locales. Using the locales manager would have done this automatically for you :cool: 

Cheers

-Leezer-

---

### Post by meriva on 2005-10-22
What do you mean for "locale manager"? :???: 

Thanks in advance.
Ciao

---

### Post by leezer3 on 2005-10-22
It's in one of the two admin menus. I'm not on the machine at the mo, so I might have got the name slightly wrong, but basically its a GUI which allows you to setup your locales config.

Cheers

-Leezer-

---

