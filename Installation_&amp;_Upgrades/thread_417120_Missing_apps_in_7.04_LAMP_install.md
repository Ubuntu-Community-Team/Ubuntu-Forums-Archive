---
title: "Missing apps in 7.04 LAMP install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by the_nite_owl on 2007-04-21
Hi All,
Warning, I am a semi-newbie so the answer might be simple but...

I just installed 7.04 x86 64, selected a LAMP installation and everything completed fine.
Being a relative newbie to Linux I chose to install the Gnome GUI to make things easier.
I then installed Webmin to help me get Apache and MySQL up and working but I cannot find them on the system.  They are not where Webmin defaults to and I have browsed the drive and cannot seem to find any files related to Apache, MySQL, PHP, Perl, etc.

Did I miss a step in the install?  Should selecting LAMP install automatically have taken care of it or should there be more steps?

Details on the system.  The main hard drive is a 120GB IDE drive with Windows XP.  I had previously partitioned this drive to provide a 50GB partition for Linux and a 2.5GB for swap all on the primary master IDE drive.  I also have a 500GB SATA drive and a SATA DVDR drive.

I had a previous install of Ubuntu 6.10 on the system and when I added in the SATA drive it screwed up Grub so I could no longer boot into Ubuntu.  So when I decided to install Feisty Fawn I used the same partitions and told the main Linux partition to reformat. 

Any thoughts?  I am just learning Linux as I go so this might be a common problem or a simple mistake but I cannot think where I did anything wrong.

Thanks.

---

### Post by bashologist on 2007-04-21
If you're looking for where your package installed it's files then maybe try this?:
```
dpkg -L <packagename>
```

Had you been following a tutorial for installing/setting up this lamp server?

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by the_nite_owl on 2007-04-21
> **bashologist said:**
> If you're looking for where your package installed it's files then maybe try this?:
```
dpkg -L <packagename>
```

Had you been following a tutorial for installing/setting up this lamp server?

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

No separate package, I just ran the Ubuntu install and selected LAMP install.  I thought that this was a package that contained all the apps in one install???

No, I was not following a tutorial as I thought it would all install in one shot then I would look into what info I would need for configuring the individual portions.

If something just failed during the install I could re-run the install and see if it works.  If the apps are not actually there I could install individually but I did not want to try an install if they were actually there and I just did not know where to find them.

---

### Post by sammyp42 on 2007-04-23
I ran into this same thing.  Thought I was going crazy.  Seems like the LAMP install of 7.04 is broken.  Too bad.  Just looked to using Ubuntu for setting up a couple of LAMP servers and ended up wasting a few hours to find out it does not to what I ask it to do (install a LAMP system when it says I select "LAMP install" at install).  Not very confidence inspiring... so, looks like my search to find a good quick streamlined minimalist LAMP server install continues...

---

### Post by the_nite_owl on 2007-04-23
> **sammyp42 said:**
> I ran into this same thing.  Thought I was going crazy.  Seems like the LAMP install of 7.04 is broken.  Too bad.  Just looked to using Ubuntu for setting up a couple of LAMP servers and ended up wasting a few hours to find out it does not to what I ask it to do (install a LAMP system when it says I select "LAMP install" at install).  Not very confidence inspiring... so, looks like my search to find a good quick streamlined minimalist LAMP server install continues...

I re-installed and it worked.
I might not have actually selected LAMP install the first time but I am not sure.
On that screen you can arrow down to lamp install and it highlights but it is not selected unless you hit the space bar and it places an asterisk in the field.  It might be that when it highlighted I assumed it was selected since there were only two options and it appeard to be a one or the other list.

Mine is working now.  Now I just have to learn how to configure it all.  Just installed Webmin to help.

---

### Post by az on 2007-04-23
> **sammyp42 said:**
> I ran into this same thing.  Thought I was going crazy.  Seems like the LAMP install of 7.04 is broken.  Too bad.  Just looked to using Ubuntu for setting up a couple of LAMP servers and ended up wasting a few hours to find out it does not to what I ask it to do (install a LAMP system when it says I select "LAMP install" at install).  Not very confidence inspiring... so, looks like my search to find a good quick streamlined minimalist LAMP server install continues...

The 7.04 LAMP install works fine.  You can't get any more streamlined than that.

---

### Post by pspcz on 2007-07-20
> **az said:**
> The 7.04 LAMP install works fine.  You can't get any more streamlined than that.

just an FYI, i had this same issue, installed twice because i thought i was going nuts

despite selecting the LAMP option in 7 server ppc install on both installations, apache, mysql and php were not installed and had to be manually installed


is there an apt-get  command for installing apache 1.3 instead of 2?


Pz

---

### Post by az on 2007-07-20
> **pspcz said:**
> just an FYI, i had this same issue, installed twice because i thought i was going nuts

despite selecting the LAMP option in 7 server ppc install on both installations, apache, mysql and php were not installed and had to be manually installed


is there an apt-get  command for installing apache 1.3 instead of 2?


Pz

What disk are you using?  Are you sure you are picking the LAMP server option and not just the base install?  Apache is version 1.3.  It is in universe and not officially supported in Ubuntu.  As well, webmin is broken and that's why there is no Ubuntu webmin package anymore.

---

### Post by pspcz on 2007-07-21
> **az said:**
> What disk are you using?  Are you sure you are picking the LAMP server option and not just the base install?  Apache is version 1.3.  It is in universe and not officially supported in Ubuntu.  As well, webmin is broken and that's why there is no Ubuntu webmin package anymore.

disk: ubuntu-7.04-server-powerpc.iso (a "community" supported product, i know)

definately using the lamp install option

we were able to install webmin, actually this helped me find out the items were not installed at all, i kept assuming they were just in some wacky location that i could not find

i planned on using webmin as a crutch and than uninstall it for security reasons, whats broke if u dont mind me  trolling for answers :)

Pz

---

