---
title: "Wine installation problems"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by mkg on 2005-05-13
Hallo again
I was trying to install wine and I get this massage

Hallo again
I was trying to install wine and I get this massage: 
Could not mark all packages for installation or upgrade

The following packages have unresolvable dependences. Make sure that all required repositories are added and and enhanced in the preferences

Winetools
Depends: xdialog but it is not installable
Depends: gtk-smooth-themes but it is not installable

Please help it is very important I hope for anyone

---

### Post by thierry on 2005-05-13
You should have a look at this page :

[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

Take the time to learn a bit about how your system is working.

You forgot to activate the Universe repository (this is where the packages are downloaded from). If you're in Synaptic go to Categories and then the second option (probably called differently in your language...) will enable you to add repositories.

Cheers :)

---

### Post by mkg on 2005-05-16
[QUOTE=thierry]You should have a look at this page :

[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")

Take the time to learn a bit about how your system is working.

You forgot to activate the Universe repository (this is where the packages are downloaded from). If you're in Synaptic go to Categories and then the second option (probably called differently in your language...) will enable you to add repositories.

Cheers :)[/QUOTE]

Good for you if you now how to do this. I still do not manage this installation. I use Kubuntu 5.04 but I tried with synaptic and kynaptic …. It is not easy to understand. If I do not succeed with this … So, can someone explain, in details pleasee

---

### Post by mkg on 2005-05-16
[QUOTE=mkg]Good for you if you now how to do this. I still do not manage this installation. I use Kubuntu 5.04 but I tried with synaptic and kynaptic …. It is not easy to understand. If I do not succeed with this … So, can someone explain, in details pleasee[/QUOTE]

Hay I made it some how and wine is starting with installation, but my suggestion to the whole community still stands. Please do this as simple as possible as let say Microsoft did it with Windows installer. It will be great step forward.

Have a nice day

p.s. I will right again don't worry

---

### Post by mkg on 2005-05-16
[QUOTE=mkg]Hay I made it some how and wine is starting with installation, but my suggestion to the whole community still stands. Please do this as simple as possible as let say Microsoft did it with Windows installer. It will be great step forward.

Have a nice day

p.s. I will right again don't worry[/QUOTE]

So, I can see that everybody is slipping  :-# , but I did not. So, I managed to install wine by my self  :-P , but thank you Thierry for your advice. It helped. I manage to install universe repository (I do not now how exactly, [-X  but I did it) Right now my main problem is how to install win98 under wine, or how to run application usually running under MS-Dos under 	WINE. I will inform you, but it would help if someone wants to give some advices.

Thank you, you lazy community  :mad:  :smile:

---

### Post by Trickyphillips on 2005-05-16
[QUOTE=mkg]So, I can see that everybody is slipping  :-# , but I did not. So, I managed to install wine by my self  :-P , but thank you Thierry for your advice. It helped. I manage to install universe repository (I do not now how exactly, [-X  but I did it) Right now my main problem is how to install win98 under wine, or how to run application usually running under MS-Dos under 	WINE. I will inform you, but it would help if someone wants to give some advices.

Thank you, you lazy community  :mad:  :smile:[/QUOTE]

I really didn't find it very hard to install the extra repositories on my first time using Ubuntu. If you just follow what it tells you, step-by-step, you'll be fine. 

I wouldn't call the Ubuntu community lazy, at all. Chua Wen Kiat put a lot of work into writing that guide. :)

---

### Post by thierry on 2005-05-16
Did you install the winesetuptk package ? If you did then typing winesetup in your terminal will enable you to either :

- create a fake Windows environment in Ubuntu ;
- use your existing Windows partition.

For your general information :

[http://www.ubuntulinux.org/wiki/UserDocumentation]("http://www.ubuntulinux.org/wiki/UserDocumentation")

When you will get used to Ubuntu you will realize it's actually easier than Windows.

Also we're not lazy. Personnally I have a lot of work even on this holiday.

---

### Post by mkg on 2005-05-17
> **thierry]Did you install the winesetuptk package ? If you did then typing winesetup in your terminal will enable you to either :

- create a fake Windows environment in Ubuntu  said:**
> http://www.ubuntulinux.org/wiki/UserDocumentation[/url]

When you will get used to Ubuntu you will realize it's actually easier than Windows.

Also we're not lazy. Personnally I have a lot of work even on this holiday.

It is I … again  :) (I think this was from a comic TV show). It is really interesting finding the solution for your self and achieve thing that you do not need desperately. That is my case starting using Linux (Kubuntu 5.04). My thinking is, I have OS that it works fine for me starting from Windows 3.11, but I would like to try to improve my self and help others to have choice, which I do not had in that time, so as an experienced user (let say almost administrator), I took my responsibility to cover empty space in so called Linux community in Macedonia. O.K. I exaggerate, but it feels good \\:D/ . Personally I do not think that you are lazy, but some of us (I start to think as a member of community, that is good :grin: ) are and some of us, especially advanced users and programmers, think that we have to now “simple things” which is not so simple for someone as me ](*,) . I have a lot of work my self, but I find time to use Kubuntu, in the way, that my surrounding will use and that is running Windows application on Linux OS. So, I’m sorry for calling you lazy, but that was only way to provoke answers from you gays.

Now, let see what I did. I manage to install wine and I think that I configure it, but I’m not sure how can I use it. I have to install local software (application) under ms-dos (it’s old, I now, but do not ask please, it is very important) located in three folders on C:\. Also I need autoexec.bat (for set clipper=f100) and config.sys (for files=100) and batch for the application let say start.bat. Those who now was working with MS-Dos now what do I have to do. If you have any information or knowledge doing this I would like to post it. It will be great. Thank you again for your time.

Goran

---

### Post by thierry on 2005-05-18
Hi Goran !

Sorry for answering late. My wife is getting very jealous about the computer...

Before trying to use Windows programs in Ubuntu please have a look at this very good thread :

[http://www.ubuntuforums.org/showthread.php?t=33183&highlight=windows]("http://www.ubuntuforums.org/showthread.php?t=33183&highlight=windows")

I tried to get the Dos command prompt with Wine but it didn't work by accessing the Windows XP partition (I don't need that). Remember that Wine is still very much under development. If you really need to use your Dos applications I suggest you try various configurations. Try copying the whole Dos files in a fake Windows environment (this would be in the /home/~/.wine folder).

Also to make it easier for someone to help you please describe your problem with details. What is your Dos program doing ? What is your configuration ?...

Good luck !

---

### Post by mkg on 2005-05-18
[QUOTE=thierry]Hi Goran !

Sorry for answering late. My wife is getting very jealous about the computer...

Before trying to use Windows programs in Ubuntu please have a look at this very good thread :

[http://www.ubuntuforums.org/showthread.php?t=33183&highlight=windows]("http://www.ubuntuforums.org/showthread.php?t=33183&highlight=windows")

I tried to get the Dos command prompt with Wine but it didn't work by accessing the Windows XP partition (I don't need that). Remember that Wine is still very much under development. If you really need to use your Dos applications I suggest you try various configurations. Try copying the whole Dos files in a fake Windows environment (this would be in the /home/~/.wine folder).

Also to make it easier for someone to help you please describe your problem with details. What is your Dos program doing ? What is your configuration ?...

Good luck ![/QUOTE]

Hallo Thierry,

Thank you very much for you suggestion. It feels nice when you now you are not alone in this and help will come. To be honest I’m not sure that I have time to “play a little bit” with Kubuntu and also I do understand things about wife and etc. Please send her an apology. So, right now I have Kubuntu installed separate machine (on Celeron 900 MHz) without any windows like partition. I did install wine and type winesetup and wine is start, but says something is wrong or near like that. What do I want to do with wine on Linux. I have old application for invoicing and reports and I still need it. I have to install dbase III also and run it. If this application can work under Kubuntu… I still think that running some virtual machine (for example vmware) on Windows is not so difficult, but under Kubuntu …. I'm confused still, but I will try to clier .... going to work

I’m going to try again in my coffee pause to do something about all of this. 

Goran

p.s. If you have any info about vmware (during the installation was trying to locate folder with kernel) do not hesitate to inform me  :)

---

### Post by thierry on 2005-05-18
Are you still using dBase III plus ? Wow ! I was programming with that 15 years ago :mad:

I'm sorry but I don't know how to use Vmware. For me Google was also a good source of information. I'm sure there is a solution...

---

### Post by mkg on 2005-05-18
[QUOTE=thierry]Are you still using dBase III plus ? Wow ! I was programming with that 15 years ago :mad:

I'm sorry but I don't know how to use Vmware. For me Google was also a good source of information. I'm sure there is a solution...[/QUOTE]

It is not my application I just use. dBase III plus ? no of course not.
Hay check this:

For today I will go around wine for now and try to install vmware instead I mean I start to install vmware and have this massage:

Trying to find a suitable vmmon module for your running kernel

None of the pre-built vmmon modules for Vmware Workstation is suitable for your running kernel. Do you want this program to try to build …….. you need to have C compiler installed on your system ………. 

I type yes of course and than next massage:

What is location of the directory of C header files that match your running kernel? [/usr/src/linux/include] 

I hit Enter

The path “/usr/src/linux/include” is not an existing directory

After this I try to locate needed directory, but I failed.

I'm stupid probably  :)

---

### Post by mkg on 2005-05-18
[QUOTE=mkg]Hallo Thierry,

Thank you very much for you suggestion. It feels nice when you now you are not alone in this and help will come. To be honest I’m not sure that I have time to “play a little bit” with Kubuntu and also I do understand things about wife and etc. Please send her an apology. So, right now I have Kubuntu installed separate machine (on Celeron 900 MHz) without any windows like partition. I did install wine and type winesetup and wine is start, but says something is wrong or near like that. What do I want to do with wine on Linux. I have old application for invoicing and reports and I still need it. I have to install dbase III also and run it. If this application can work under Kubuntu… I still think that running some virtual machine (for example vmware) on Windows is not so difficult, but under Kubuntu …. I'm confused still, but I will try to clier .... going to work

I’m going to try again in my coffee pause to do something about all of this. 

Goran

p.s. If you have any info about vmware (during the installation was trying to locate folder with kernel) do not hesitate to inform me  :)[/QUOTE]


Finally located thanks to the community. About that lazy ... yes I was wrong  :wink:

---

### Post by verbalshadow on 2005-05-18
[QUOTE=mkg]It is not my application I just use. dBase III plus ? no of course not.
Hay check this:

For today I will go around wine for now and try to install vmware instead I mean I start to install vmware and have this massage:

Trying to find a suitable vmmon module for your running kernel

None of the pre-built vmmon modules for Vmware Workstation is suitable for your running kernel. Do you want this program to try to build …….. you need to have C compiler installed on your system ………. 

I type yes of course and than next massage:

What is location of the directory of C header files that match your running kernel? [/usr/src/linux/include] 

I hit Enter

The path “/usr/src/linux/include” is not an existing directory

After this I try to locate needed directory, but I failed.

I'm stupid probably  :)[/QUOTE]
 did you apt-get the kernel sources/headers?


why use a VMware at all there are good free virtual machines out there Bochs and Qemu come to mind.

Bochs
bochs.sourceforge.net/

Qemu
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
not sure if it in the Ubuntu Repositories but if not the Debian testing and unstable has a version of it
Qemu Launcher- this makes things easier for us former windows users.
[http://emeitner.f2o.org/projects/qemu-launcher/](http://emeitner.f2o.org/projects/qemu-launcher/)

secondly if all you want to do is run DOS programs you don't need wine or VMware, look at 
DOSBox or the other DOS specfic emulators.

---

### Post by mkg on 2005-05-18
[QUOTE=mkg]Hallo Thierry,

Thank you very much for you suggestion. It feels nice when you now you are not alone in this and help will come. To be honest I’m not sure that I have time to “play a little bit” with Kubuntu and also I do understand things about wife and etc. Please send her an apology. So, right now I have Kubuntu installed separate machine (on Celeron 900 MHz) without any windows like partition. I did install wine and type winesetup and wine is start, but says something is wrong or near like that. What do I want to do with wine on Linux. I have old application for invoicing and reports and I still need it. I have to install dbase III also and run it. If this application can work under Kubuntu… I still think that running some virtual machine (for example vmware) on Windows is not so difficult, but under Kubuntu …. I'm confused still, but I will try to clier .... going to work

I’m going to try again in my coffee pause to do something about all of this. 

Goran

p.s. If you have any info about vmware (during the installation was trying to locate folder with kernel) do not hesitate to inform me  :)[/QUOTE]

For those who read this thread I want to inform you that I managed to install vmware. Wine was to let say to tricky for me ... for now 

Keep up the good work we are closer to success

Goran

---

### Post by mkg on 2005-05-18
[QUOTE=verbalshadow]did you apt-get the kernel sources/headers?


why use a VMware at all there are good free virtual machines out there Bochs and Qemu come to mind.

Bochs
bochs.sourceforge.net/

Qemu
[http://fabrice.bellard.free.fr/qemu/](http://fabrice.bellard.free.fr/qemu/)
not sure if it in the Ubuntu Repositories but if not the Debian testing and unstable has a version of it
Qemu Launcher- this makes things easier for us former windows users.
[http://emeitner.f2o.org/projects/qemu-launcher/](http://emeitner.f2o.org/projects/qemu-launcher/)

secondly if all you want to do is run DOS programs you don't need wine or VMware, look at 
DOSBox or the other DOS specfic emulators.[/QUOTE]

This is new for me so I'm going to try those two free virtual machines. About DOSBox ... I'm not very sure, but if you say so I will try. To be honest I think windows is still my number one OS.

Thank you again.

---

### Post by mkg on 2005-05-18
[QUOTE=mkg]This is new for me so I'm going to try those two free virtual machines. About DOSBox ... I'm not very sure, but if you say so I will try. To be honest I think windows is still my number one OS.

Thank you again.[/QUOTE]

p.s. I can see that QEMU do not support Kubuntu 5.04. I'm not sure that will work. Any advice ?

---

