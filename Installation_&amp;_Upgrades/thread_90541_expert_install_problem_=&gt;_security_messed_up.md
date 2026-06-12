---
title: "expert install problem =&gt; security messed up"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by peterp on 2005-11-15
When I first installed ubuntu 5.10 on borrowed cdrom everything works as it should but then freebsd came and messed up my disk geometry so I have to reinstall everything. Then I bought benq dw1640 dvd burner and (tried)installing ubuntu again. After long day of trying I find out that ubuntu dont like my dvd drive because standard install doesnt have dma turned on for drive as default. 

This problem is described here: [http://www.ubuntuforums.org/showthread.php?t=72056](http://www.ubuntuforums.org/showthread.php?t=72056) 
[http://bugzilla.ubuntu.com/show_bug.cgi?id=16901](http://bugzilla.ubuntu.com/show_bug.cgi?id=16901)

Then I installed again using expert install mode (it takes few times to find out how it works) because in that mode I can set dma=on for my drive. There were some issues about what to choose and one bug which I describe now. 
When it comes to set root password I typed in once and when I retyped password and pressed enter they didnt match. Of course my mistake but I forgot original one and there was no way to go back. If I started root password step again it only goes to screen where I should retype (or reenter) original password. Then I had to quit installing and everything do once again.

This was a minor problem but then after install I logged in as user (created during install) and happend exactly that:
[http://ubuntuforums.org/showthread.php?t=75767](http://ubuntuforums.org/showthread.php?t=75767)

With one difference that it cant be fixed as this guy described. I restarted to recovery mode logged in as root and started gnome where I could change user properties with gui utility but there was no option like I remembered before for allowing user to perform administrative tasks like installing programs. Then I take a look on /etc/group and there was no admin group.
After few restarts and adding/removing user suddenly appeared that option(I have no idea how that happend) but tools in system/administrative menu wasnt still accessible. My last attempt(I was gettin crazy) was to add user to  root group but it wasnt helpfull either.

I will realy appreciate some help because I dont have to much time to play with linux (If I have time I will be probbably using gentoo). I think that many people choose ubuntu because it is just "working" in most cases and standard install doesnt have 5GB as for suse or mandriva.

Thanks.
peter

---

### Post by peterp on 2005-11-23
After my problems with expert install i finally ended up with server-expert install mode. I find out that if i not say yes when install program ask me to copy remaining packages from cd to disk then post-install ends in a middle of nowhere, but after restart it succesfully boot to shell. So i said yes and installed it without problems.

Then i installed xubuntu-desktop because gnome is sluggish and i like xfce. Everything works just fine only one thing bothers me. Sudo isnt working anymore so I uninstalled it and I will fix it later.

I decided that boot time must be shorter so I followed this howto [http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot+time](http://ubuntuforums.org/showthread.php?t=89491&highlight=speed+boot+time)
and the result is nice. Ubuntu starts faster than my winxp and thats really something. In a few second i am in shell (never counted but about 10 seconds) and after startx command about 2-3 seconds to start xfce and i dont even started to tweak kernel.

Now I am working on kernel config with nice xconfig gui as described here [http://www.ubuntuforums.org/showthread.php?t=84174&highlight=xconfig](http://www.ubuntuforums.org/showthread.php?t=84174&highlight=xconfig) and after few experiments I see big potential in tweaking here. For example memory used can be drastically decreased or desktop response time can be improved. It takes me some time to acceptably understand most options in kernel config but good is that you need to do it only once, because with new kernel you can use stored config from older one.

---

