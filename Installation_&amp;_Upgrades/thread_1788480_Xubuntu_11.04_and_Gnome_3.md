---
title: "Xubuntu 11.04 and Gnome 3"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by irv on 2011-06-22
When Ubuntu 11.04 came out, I tried it with Gnome 3 but had some issues because of Unity not playing well with Gnome 3.
I was wondering if anyone has try Gnome 3 with Xubuntu which uses Xfce? If I know it wouldn't break my system I would give it a try.

---

### Post by irv on 2011-06-23
Isn't there just one person out here that has Xubuntu 11.04 that has tried it with Gnome 3? If not, do I have to be the genie pig?

---

### Post by cbowman57 on 2011-06-23
Shouldn't be a problem, use the installation instructions here: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/) & add ppa:ricotz/testing, you shouldn't have any problems.  I tried xfce4-panel on my gnome shell & it worked fine.

---

### Post by irv on 2011-06-24
> **cbowman57 said:**
> Shouldn't be a problem, use the installation instructions here: [http://ugr.teampr0xy.net/](http://ugr.teampr0xy.net/) & add ppa:ricotz/testing, you shouldn't have any problems.  I tried xfce4-panel on my gnome shell & it worked fine.

For the record, I followed the link in your post; downloaded the script file; ran it and did the install; rebooted and am now running Gnome 3. It looks like everything is running OK but lets give it some time.
Now my question is, Now that I am running Gnome 3 and not Xfce for a desktop, am I using Xubuntu or Ubuntu? Silly question I know.

---

### Post by irv on 2011-06-24
I thought I would just post a screen shot of my new Gnome 3 Desktop now that I have it running on Xubuntu 11.04.
[ATTACH]195860[/ATTACH]

---

### Post by cbowman57 on 2011-06-24
> **irv said:**
> I thought I would just post a screen shot of my new Gnome 3 Desktop now that I have it running on Xubuntu 11.04.
[ATTACH]195860[/ATTACH]

Looks nice, after posting this yesterday I opened up UCK myself, downloaded a 64-bit version of Xubuntu and did a respin that I haven't tried yet, it's working name is gNatty X. :)

If you want the theme & extension support I think you'll have to install from git or use ricotz/testing to the files in the thumbnail.

---

### Post by irv on 2011-06-24
OK, my first problem came up. Many of the games I have installed will not run. I get the same error with all of them. I tried removing them and then re-installing them but I still get this error: 
[ATTACH]195884[/ATTACH]

---

### Post by cbowman57 on 2011-06-24
There is a workaround if you have the patience to look for it, that behavior is not exclusive to Xubuntu.

My simple fix is to force a downgrade to the 2.32 gdm, for some reason gdm 3.0 introduced this problem.  Using synaptic, locate gdm, highlight it, then select 'Package' from the menu > Force Version > gdm 2.32 ***.  After forcing the downgrade you'll want to lock it to prevent it from being overwritten.  If you do an update using anything other than synaptic though (i.e. apt-get) it will be overwritten.  If you use aptitude from the command line you can lock it also using **sudo aptitude hold gdm** then you can do command line updates using aptitude without upgrading the gdm.

If you don't want to change the gdm, you can search for solutions, it's an environment problem.  I think it can be cured with some editing of the .bashrc file but not positive.

---

### Post by irv on 2011-06-24
> **cbowman57 said:**
> There is a workaround if you have the patience to look for it, that behavior is not exclusive to Xubuntu.

My simple fix is to force a downgrade to the 2.32 gdm, for some reason gdm 3.0 introduced this problem.  Using synaptic, locate gdm, highlight it, then select 'Package' from the menu > Force Version > gdm 2.32 ***.  After forcing the downgrade you'll want to lock it to prevent it from being overwritten.  If you do an update using anything other than synaptic though (i.e. apt-get) it will be overwritten.  If you use aptitude from the command line you can lock it also using **sudo aptitude hold gdm** then you can do command line updates using aptitude without upgrading the gdm.

If you don't want to change the gdm, you can search for solutions, it's an environment problem.  I think it can be cured with some editing of the .bashrc file but not positive.

This did the trick. Thanks again for all the help. I do like Gnome 3 and I wanted to keep using it until I see what Ubuntu is going to do with the next release. I want to see where Unity is going to go and also if Gnome 3 will be offered with the next release. I don't think so, but I am hoping they do. Time will tell.

---

### Post by cbowman57 on 2011-06-24
Unity will be built to use Gnome 3.0, but not the shell.  The shell will be available through the repositories for Ubuntu 11.10

Personally I have no hope for Unity, it just doesn't flow like gnome-shell does for me.

Here's a peek at my desktop using gnome shell.

---

### Post by tele1953 on 2011-11-18
I installed Gnome 3 thu Xubuntu with no problems.For some reason my compaq cq56 did not like Ubuntu it was always freezing up so I installed Xubuntu,then I updated then terminal sudo update install gnome shell.works perfect in fact I done a aptoncd.

---

