---
title: "Package Installation Help; Hotway (POP3/SMTP Hotmail)"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by total-noob on 2005-03-06
Being a total Linux illiterate and having a very short endeavor with Linux after trying out the Ubuntu Live CD, I am now trying to make my harddisk installation work the way I would like. Most of it works just fine, but moving away from Windows I still need to fix a few things, one of them Hotmail support for Evolution. I know this can be achieved with Hotway POP3 to HTTPmail demon - I have tried it and it works fine. Unfortunately the version included for Warty is old (0.7.1) and does not support sending e-mail, so i will need to use the version to be included with Hoary (0.8.2):

[http://higgs.djpig.de/ubuntu/www/hoary/source/hotway](http://higgs.djpig.de/ubuntu/www/hoary/source/hotway)  

I see that I can download a source package, but having only a few weeks of experience with Ubuntu and only used Synaptic until now, I have no idea what to do with these downloads. Could someone give me some down-to-earth guidance on installing this version of Hotway? Which of the packages should I download? Which commands to use? This version includes both POP3 conversion and SMTP conversion - are separate installation procedures needed?

---

### Post by DJ_Max on 2005-03-07
This package is in the Ubuntu "Universal" Repositories. 
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

After you add those, do this via terminal.
```
sudo apt-get install hotway
```

The root password is your user account password aswell.

---

### Post by total-noob on 2005-03-07
Thanks, sounds right to me.  But just a little clarification: I would need to add *Hoary* repositories right? Otherwise I would not be getting the latest version? Can I just add these two lines to /etc/apt/sources.list, while _also_ having the Warty Universe repositories?

```
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
```

---

### Post by DJ_Max on 2005-03-07
Well, not, you can't use the Hoary repositories unless you are running Hoary. Your options are to check the Backports. [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

Or compile the package hotway manually.

---

### Post by dewey on 2005-03-07
The ubuntu backport project mentioned above is a project that ports Hoary packages, which are newer versions, to work with Warty and be completely compatible.

It allows you to update to firefox 1.0 for example, without having to compile from source.

---

### Post by total-noob on 2005-03-08
Hmmm...  :?  I know the long term solution is to upgrade to Hoary when available, but for now I feel a bit stuck. I am not much into compiling myself (except if given some guidance on this matter) and I can not really find a more recent version of Hotway in the backport project. Should I be giving up on this one?  :|

---

### Post by DJ_Max on 2005-03-08
[QUOTE=total-noob]Hmmm...  :?  I know the long term solution is to upgrade to Hoary when available, but for now I feel a bit stuck. I am not much into compiling myself (except if given some guidance on this matter) and I can not really find a more recent version of Hotway in the backport project. Should I be giving up on this one?  :|[/QUOTE]
Compiling software from the source is my prefered way of install apps since it allows for greater customization, and it's faster since it's suited to your specifc system.

It's fairly easy, you'll need certain libraries, most are included with the base install of Ubuntu, GNU C (gcc) GNU C++(g++). Plus others, depending on the program you're trying to install.

It's like this, first you decompress the archive, move into the new directory, run "./configure", which checks that you have everything needed, and makes a some files. You then run "make", then you do "make install". You'll need root privileges for make install.

Need any more help let me know.

---

### Post by mirtux on 2005-03-24
Hi,
  i would like to know how is possible to configure hotway for use, for example, with Thunderbird. Is it enough to read the /usr/share/doc/hotway/README.gz file to get it installed?

Thanks,
MC

---

### Post by puccaso on 2006-03-22
ok
so i have used hotwayd for ages
and i'm happy people have been using it too

but now, i got windows live mail
and i am assuming the folders have changed or something
so now i need to get 

oh ye wait
i got windows live and a windows live domain thingi (google it) 
and i cant acess my mail via hotwayd

any ideas?

---

