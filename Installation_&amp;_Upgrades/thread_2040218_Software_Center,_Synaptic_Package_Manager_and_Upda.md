---
title: "Software Center, Synaptic Package Manager and Update Manager NOT WORKING - 11.04"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by abalnt on 2012-08-10
Dear all,@[[Olle Wiklund]("http://ubuntuforums.org/member.php?u=571173")], @[[BC59]("http://ubuntuforums.org/member.php?u=1498360")], @[[[COLOR=#DD4814]**matt_symes**[/COLOR]]("http://ubuntuforums.org/member.php?u=1067998")], @[[plucky]("http://ubuntuforums.org/member.php?u=317619")], @[[[COLOR=#DD4814]**wildmanne39**[/COLOR]]("http://ubuntuforums.org/member.php?u=508533")],  @[[dniMretsaM]("http://ubuntuforums.org/member.php?u=1268161")], @[[[COLOR=#DD4814]**mörgæs**[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")]

Ubuntu software center is not working. I want to install skype but if i  type skype in the search button, it keeps on loading.I am using ubuntu  11.04
Please help...

I am also facing a problem with Synaptic Package Manager and Update Manager

[B]
Trying to run the update manager returned the following result:
[/B]
[SIZE=3]An error occurred[/SIZE]
The following details are provided:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
[B]
Trying to run the update manager returned the following result:[/B]

 Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

**The problem started after I tried to upgrade from Ubuntu 11.04 to 11.10.  I got the message about the availability of a new version and I clicked upgrade now. The process started and the first two tasks in the list completed successfully but then suddenly the whole upgrade status box disappeared and the rest of system seemed to function normally. After that I tried to install skype and have not been able to do so.**

I am more of a new user to Ubuntu. Though I installed it a while ago, I have been using Windows only as I have both the OS on my Laptop. Only recently I started using Ubuntu.

I tried to install using the terminal by this command[sudo apt-get install skype] but it returned the following message:

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I tried using sudo apt-get update && sudo apt-get upgrade but I got the following error

Fetched 1,144 kB in 41s (27.3 kB/s)                                            
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_oneiric-security_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Now I don't know what to do next and how should I rectify the problem. Please help!

---

### Post by oldos2er on 2012-08-10
[http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/](http://ihaveapc.com/2011/05/how-to-fix-problem-with-mergelist-varlibaptlists-error-in-ubuntu-11-04/)

---

### Post by abalnt on 2012-08-11
Dear Ann,

Thank you so much. Your solution worked like MAGIC. :PMy laptop is working fine now!
God bless you.

:):):)

---

### Post by oldos2er on 2012-08-11
You're welcome. Enjoy Ubuntu!

---

### Post by donaldt on 2012-08-13
I have a similar, but not identical problem.  My Ubuntu 12.04 update manger will lock up during updates and I have to re-boot the computer to regain control.

I've tried several fixes gleaned from others with similar problems that have helped.  For example, I can now make update manager work if I go to the terminal and use [sudo apt-get update && sudo apt-get dist-upgrade] prior to launching update manager.  Only then will it finish the installation of the proposed update and software installation.  If I launch update manager without first running the terminal commands, it continues to hang about 2/3 the way through.

I just tried the fix that Ann proposed to the 11.04 user that had several issues.  I can't try that until the next time I'm offered another update.  Is there enough similarity to the two problems that it is likely to work, or is there another solution to my problem?

Thanks if you can help!

donaldt

---

