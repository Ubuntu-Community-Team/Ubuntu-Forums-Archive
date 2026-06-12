---
title: "Two partions/OS'es, one home folder."
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by epqr on 2008-11-09
this possible? to have two ubuntu-versions installed on different partions, while they share one home folder? i know i could just save things to the same place, but it would be so much easier if they had the same home folder, so that it don't matter which version i am on.

---

### Post by Pumalite on 2008-11-09
You can do it, but they have to have different usernames and passwords

---

### Post by epqr on 2008-11-09
OK, so if i like go to home folder on my one OS, i will find the same documents and folder as on the other os?

---

### Post by bulldog on 2008-11-09
Not really,you will have two folders in your /home.
You can copy your documents etc. to both folders,but it still remain two different folders.
So if you make a change in one folder using 8.04,it will not automaticly apply in the folder when you use 8.10.

---

### Post by oledocmeth on 2008-11-09
Yes, I think this is possible.  I would set up partitions like this --

Mount Point  what is in partition             Size
/boot        GRUB                             about 300MB - 500MB (for multiple kernel versions)
swap         swap                             about 1 to 5GB
/            OS V1 - Say 8.04                 at least 5GB
/altOS       OS V2 - maybe 8.10               at least 5GB
/home        /home                            however big you want

NOTE: "/altOS" is something I made up, can be anything
When you are creating the mount tables for OS V2, you will swap the / and /altOS mount points.  This is done during the partitioning section of installation procedure.

PS NOTE:  I made a seperate /boot partition in ext3 format because it solved a lot of Ubuntu 8.10 GRUB errors during boot.

---

### Post by bulldog on 2008-11-09
> **oledocmeth said:**
> Yes, I think this is possible.  I would set up partitions like this --

Mount Point  what is in partition             Size
/boot        GRUB                             about 300MB - 500MB (for multiple kernel versions)
swap         swap                             about 1 to 5GB
/            OS V1 - Say 8.04                 at least 5GB
/altOS       OS V2 - maybe 8.10               at least 5GB
/home        /home                            however big you want

NOTE: "/altOS" is something I made up, can be anything
When you are creating the mount tables for OS V2, you will swap the / and /altOS mount points.  This is done during the partitioning section of installation procedure.

PS NOTE:  I made a seperate /boot partition in ext3 format because it solved a lot of Ubuntu 8.10 GRUB errors during boot.

Making one /home is certainly possible,but that's not his point.
He wants to have the same content eg. using the same folder within his /home.
This can create some problems when he uses ubuntu and kubuntu with the same username and password.

When you want to use two different ubuntu releases,you should use different usernames and passwords for each release.
This will create two different folders in your /home.
You can copy data between them,but they are NOT the same folder for each distro.

---

### Post by epqr on 2008-11-09
So it will be like this: in the home folder there will be two folders called "user1" and "user2"? os1; /home/user1 os2; /home/user2

and there is no way to make os1 and os2 use the same folders as default?

---

### Post by bulldog on 2008-11-09
> **epqr said:**
> So it will be like this: in the home folder there will be two folders called "user1" and "user2"? os1; /home/user1 os2; /home/user2
Yes.

---

### Post by epqr on 2008-11-09
> **bulldog said:**
> Yes.

and there is no way to make os1 and os2 use the same folders as default?

what would happpen is i used the same username in two distroes+

---

### Post by Ng Oon-Ee on 2008-11-09
> **epqr said:**
> So it will be like this: in the home folder there will be two folders called "user1" and "user2"? os1; /home/user1 os2; /home/user2

and there is no way to make os1 and os2 use the same folders as default?

When you talk about different ubuntu 'versions', what versions are you talking about exactly? As previously mentioned, Ubuntu and Kubuntu would probably be a crap-shoot, incompatibility between settings files etc.

On the other hand, I'm running Hardy Heron and Intrepid Ibex with the same home partition (and same username). No real bugs yet, but that's mainly because the versions for the various softwares are quite equivalent. As the software in Ibex gets updated I'd have to scratch this arrangement I think.

One nifty solution (which I haven't tried yet, but got from someone else in another forum) is to copy out the data directories and those of programs that you know aren't very different between versions (Firefox 3 on both installs, for example, you could then copy out the .mozilla folder in your home folder. Then, both your home folders could symlink to the moved directories.

I'd suggest that this be done with all the 'data' directories (Desktop, Music, etc.) as well as those of more stable applications (.mozilla, .purple which contains your Pidgin settings, .pulse if you use custom pulseaudio settings). Don't do this with regularly updated/currently under development software like Wine, Compiz...

For example (with the Desktop folder, in my /home, which is on a separate partition, I'd have these folders (hope this turns out the way I intend).

home
  ngoonee
    Desktop -> symlinked to /home/symlinked/Desktop
  ngoonee2
    Desktop -> symlinked to /home/symlinked/Desktop
  symlinked
    Desktop -> contains the actual contents of your Desktop

Of course, file permissions may be an issue. I think the first ID you use in any Ubuntu install is assigned an ID of 1000, so even if you're using different ID names, they could still have the same permissions since their numerical IDs are the same. Otherwise you'd have to make sure both IDs match in their numerical value.

---

### Post by Ng Oon-Ee on 2008-11-09
> **epqr said:**
> and there is no way to make os1 and os2 use the same folders as default?

what would happpen is i used the same username in two distroes+

Ah, we posted at the same time almost :)

Basically, your home folder contains a TONNE of hidden folders, for most of your programs, which contain settings.

So, for example, if in one install you're using an older version of a particular program and in another you're using a newer version, there's a chance that when upgrading versions the settings files have changed in some way. This would likely break your program in some way.

For example, I use a file synchronizer called Unison. Over the versions, they add new versions to the settings files which I can set. If I set a newer option to automatically detect whether the files I'm synchronizing point to unmounted drives, and try to run an older version of Unison using those same settings files, it would just quit (didn't even give me an error message I believe).

Again, for pure data it would be fine. This is mainly a worry for your program settings. Try opening your home folder (/home/<your_name>/) in Nautilus, press Ctrl-H to view hidden files, and check out the amount of things that's stored there :D

---

### Post by epqr on 2008-11-09
> **Ng Oon-Ee said:**
> Ah, we posted at the same time almost :)

Basically, your home folder contains a TONNE of hidden folders, for most of your programs, which contain settings.

So, for example, if in one install you're using an older version of a particular program and in another you're using a newer version, there's a chance that when upgrading versions the settings files have changed in some way. This would likely break your program in some way.

For example, I use a file synchronizer called Unison. Over the versions, they add new versions to the settings files which I can set. If I set a newer option to automatically detect whether the files I'm synchronizing point to unmounted drives, and try to run an older version of Unison using those same settings files, it would just quit (didn't even give me an error message I believe).

Again, for pure data it would be fine. This is mainly a worry for your program settings. Try opening your home folder (/home/<your_name>/) in Nautilus, press Ctrl-H to view hidden files, and check out the amount of things that's stored there :D

Ah, i see. obviously this will be a problem. i guess i could just make a folder under here again (/home/user/PureData) and then put documents, pictures etc. there. it won't be as easy, but probably doesnt matter to much.. 

to answer you other post, i am thinking about installing two gnome ubuntu distroes (probably 8.10 on both, maybe one with 8.04 or one with another ubuntu-like distro), but with different appearance. like on the first i am going to have pretty clean standard desktop, while on the other im going to have a dock, other tweaks etc.

---

### Post by Ng Oon-Ee on 2008-11-09
> **epqr said:**
> Ah, i see. obviously this will be a problem. i guess i could just make a folder under here again (/home/user/PureData) and then put documents, pictures etc. there. it won't be as easy, but probably doesnt matter to much.. 

to answer you other post, i am thinking about installing two gnome ubuntu distroes (probably 8.10 on both, maybe one with 8.04 or one with another ubuntu-like distro), but with different appearance. like on the first i am going to have pretty clean standard desktop, while on the other im going to have a dock, other tweaks etc.

If both were 8.10 (and I assume one is for messing around and the other is for stability) you shouldn't have a problem sharing the same home folder. Just use the same User ID.

The reason for this is that with exactly the same Ubuntu version, the programs would all be the same version exactly, so compatibility problems would not arise. Also, I'm thinking your 'messing around' install would have additional programs, but as long as those are not manually-installed upgrades on something you have in your stable install, no problem.

For non-ubuntu distros, I wouldn't recommend it. Even for 8.04, it will work for now (I'm doing it) but I'm pretty sure in 6 months things would have changed enough to break some programs.

So my advise would be, both the installs should be the same Ubuntu version. And just be careful about what you install that is not 'latest-version-on-synaptic'. For example, once Thunderbird 3 comes out, if you're an early adopter and install an RC of that but keep the Ubuntu version in the other install, if they're both using '.mozilla-thunderbird' for their settings you'll be sure to have problems.

---

### Post by epqr on 2008-11-09
> **Ng Oon-Ee said:**
> If both were 8.10 (and I assume one is for messing around and the other is for stability) you shouldn't have a problem sharing the same home folder. Just use the same User ID.

The reason for this is that with exactly the same Ubuntu version, the programs would all be the same version exactly, so compatibility problems would not arise. Also, I'm thinking your 'messing around' install would have additional programs, but as long as those are not manually-installed upgrades on something you have in your stable install, no problem.

For non-ubuntu distros, I wouldn't recommend it. Even for 8.04, it will work for now (I'm doing it) but I'm pretty sure in 6 months things would have changed enough to break some programs.

So my advise would be, both the installs should be the same Ubuntu version. And just be careful about what you install that is not 'latest-version-on-synaptic'. For example, once Thunderbird 3 comes out, if you're an early adopter and install an RC of that but keep the Ubuntu version in the other install, if they're both using '.mozilla-thunderbird' for their settings you'll be sure to have problems.


yeah thats exactly what im thinking about.

so what do i do? just install it on two different partions, then mount one of the partions as /home for both of the "versions" (say i use 8.10 on both), and use the same username? simple as that?

---

### Post by oledocmeth on 2008-11-09
Sorry, but I never had a problem between KDE or GNOME as they like to hide their configs in different locations (ie .kde/.kde4 or .gnome2 and .gconf)

---

### Post by Ng Oon-Ee on 2008-11-09
> **epqr said:**
> yeah thats exactly what im thinking about.

so what do i do? just install it on two different partions, then mount one of the partions as /home for both of the "versions" (say i use 8.10 on both), and use the same username? simple as that?

Ah, sorry, I thought you were familiar with this. I assume you're starting from scratch (blank system).

First, the partitioning, you need at least 3 partitions, one for /home, and one each for each of your installs.

Secondly, setup the first install. You'll have to use manual partitioning to designate its own partition as root (/) and the home partition as home (/home). Setup your username. Your /home should then have /home/<your_name> in it.

Next, setup the second install. Use manual partitioning again and select the empty partition as root (/) and the home partition as to be mounted as home (/home). Do NOT format the /home partition, just specify it to be mounted as /home. In your setup, specify the same username.

I can't remember if I get UID errors. You may need to open nautilus as root (sudo nautilus) and change the permissions for the root folder to your (alphabetical) ID. Do NOT make a habit of opening nautilus as root though, it can lead to VERY BAD THINGS happening. Found out the hard way :)

> **oledocmeth said:**
> Sorry, but I never had a problem between KDE or GNOME as they like to hide their configs in different locations (ie .kde/.kde4 or .gnome2 and .gconf)

Ah, I don't know about that, as I've never gotten KDE, from Kubuntu or Fedora, to work satisfactorily for me. If so, Kubuntu 8.10 and Ubuntu 8.10 should co-exist reasonably well.

---

### Post by epqr on 2008-11-09
> **Ng Oon-Ee said:**
> Ah, sorry, I thought you were familiar with this. I assume you're starting from scratch (blank system).

First, the partitioning, you need at least 3 partitions, one for /home, and one each for each of your installs.

Secondly, setup the first install. You'll have to use manual partitioning to designate its own partition as root (/) and the home partition as home (/home). Setup your username. Your /home should then have /home/<your_name> in it.

Next, setup the second install. Use manual partitioning again and select the empty partition as root (/) and the home partition as to be mounted as home (/home). Do NOT format the /home partition, just specify it to be mounted as /home. In your setup, specify the same username.

I can't remember if I get UID errors. You may need to open nautilus as root (sudo nautilus) and change the permissions for the root folder to your (alphabetical) ID. Do NOT make a habit of opening nautilus as root though, it can lead to VERY BAD THINGS happening. Found out the hard way :)



Ah, I don't know about that, as I've never gotten KDE, from Kubuntu or Fedora, to work satisfactorily for me. If so, Kubuntu 8.10 and Ubuntu 8.10 should co-exist reasonably well.


Yeah that was partly what i meant. i thought it would be enough with two partitions, but that doesn't matter. i will try it out soon.

thank you very much for your help :D

---

