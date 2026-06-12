---
title: "Upgrade 6.06 Fails"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by TennTux on 2008-03-01
Tried to upgrade but following documentation doesn't seem to work.

I've been using 6.06 LTS (dapper) for a while and have decided to upgrade to 7.10 (gutsy).

From what I have seen I need to first upgrade to 6.10 (edgy). *Ok I can try that*.

Looking at the ubuntu site I checked out the upgrade link. It said I should use the update manager to update all my installed software then it should give me the option to upgrade after doing another check. All it would do is tell me "Your system is up-to-date".

Next I went looking for better documentation and found the page for EdgyUpgrades which covers 6.06 to 6.10. Sounds promising... It recommends using the following from the command line.

```
gksu "update-manager -c"
```

This starts the software updates app. With the following message in the command prompt.
```
warnings.warn("apt API not stable yet", FutureWarning)
```

It performs a check and still does not give me the option for upgrading???

Did I miss-read the documentation?
Where do I go from here?

---

### Post by Rocket2DMn on 2008-03-01
I wouldn't try to upgrade from 6.06->6.10->7.07->7.10
Doing one upgrade is a hassle and can sometimes break things (which can be fixed, it's just a pain in the butt when it happens), especially because you've been using Dapper for so long and have it well customized.  
Going all the way to 7.10 would almost certainly cause problems, so I would either just install fresh using a Gutsy install cd, or just wait until Hardy gets released next month (it's the next LTS release) and do a fresh install then.

---

### Post by TennTux on 2008-03-01
> **Rocket2DMn said:**
> I wouldn't try to upgrade from 6.06->6.10->7.07->7.10
Doing one upgrade is a hassle and can sometimes break things (which can be fixed, it's just a pain in the butt when it happens), especially because you've been using Dapper for so long and have it well customized.  
Going all the way to 7.10 would almost certainly cause problems, so I would either just install fresh using a Gutsy install cd, or just wait until Hardy gets released next month (it's the next LTS release) and do a fresh install then.

If I will be able to upgrade all the way from Dapper to Hardy in one swell foop I can live with that. I was just that everything I've read said that I needed to upgrade through each version. I'll check it out when Hardy is released. Thanks a bunch.

---

### Post by Rocket2DMn on 2008-03-01
That is correct, you do have to go through each version which is why I don't recommend it, but rather, do a fresh install instead.  I have heard about the possibility of an LTS->LTS upgrader that would take you direct from Dapper to Hardy, but I doubt it will be ready by the time Hardy is out.  So maybe from Hardy LTS -> Hardy+1 LTS (in another 2 years).  So again, I foresee a fresh install in your future :)

---

### Post by TennTux on 2008-03-01
Ah. Not quite what I was looking for. I guess I'll have to continue looking to see how to get the upgrade(s) to work. I can live with this machine being in an indefinite state for a while. 

If my backup position is to reinstall then I might as well try to do the upgrades.

As I see it my biggest problem at this point is getting the upgrade to start. Update manager doesn't seem to be enabling the upgrade even when I use the [COLOR="Blue"]gksu "update-manager -c"[/COLOR] command line.

---

### Post by Shazaam on 2008-03-01
TennTux......
How much room do you have on your drive(s)? Would a fresh Gutsy (or Hardy) install alongside Dapper work for you?

---

### Post by TennTux on 2008-03-01
While I'm using only about 1/8th of my root partion on this system I have a few goals. The first is I have things setup the way I like them. For example: Themes, uid, ssh and other stuff. The second is, while I have some experience with Linux I could use some more. The third is I have two systems and I'm using the first one to work through issues as prep for the second. So I'm kind of interested in working through the upgrade issues if possible.

---

### Post by Rocket2DMn on 2008-03-01
Your configurations are stored in your /home/[username] directory, so if you back that up, do a fresh install, then restore the backup all your configurations will be there.  You will just have to reinstall programs, re-enable things like ssh and remote desktop, and other stuff that's not specific to your user login.
Working your way through an upgrade will not teach you anything about linux, it will probably just piss you off.  Doing a fresh install and having to redo some stuff is a good way to learn, but you won't have to tweak all your preferences because a lot of stuff is stored in your /home directory.  If you open nautilus and do CTRL+H you will see a bunch of hidden directories starting with a period - most of these are configuration directories for programs.

If you're really set on upgrading, I think you can ignore the warning that appears in the terminal since it's just that, a warning (not an error).  Can you show a print screen of exactly what happens when you try to upgrade versions?

---

### Post by TennTux on 2008-03-01
> **Rocket2DMn said:**
> If you're really set on upgrading, I think you can ignore the warning that appears in the terminal since it's just that, a warning (not an error).  Can you show a print screen of exactly what happens when you try to upgrade versions?

I am kind of attached to upgrading. Assuming I get it right I will attach 2 images. The first while "Software Updates" is performing it's checks and the second is what I get after it finishes the check. I would happily ignore the warning except I am not given an option to upgrade. (And that is the core of my problem).

---

### Post by TennTux on 2008-03-01
I'll try again to attach the print screens

---

### Post by Rocket2DMn on 2008-03-01
Is it possible to run the update manager from System->Adminstration->Update Manager like it is nowadays?
I wouldn't suggest doing the apt-get upgrade that is listed on the page, so all I can think of is to get your hands on an Edgy upgrade disc and run the upgrade from there as the guide says.
I guess you could post your sources.list file, but I can't think of anything being wrong with it that would cause this problem.  Post it anyway:
```
cat /etc/apt/sources.list
```

---

### Post by TennTux on 2008-03-01
> **Rocket2DMn said:**
> Is it possible to run the update manager from System->Adminstration->Update Manager like it is nowadays?
I wouldn't suggest doing the apt-get upgrade that is listed on the page, so all I can think of is to get your hands on an Edgy upgrade disc and run the upgrade from there as the guide says.
I guess you could post your sources.list file, but I can't think of anything being wrong with it that would cause this problem.  Post it anyway:
```
cat /etc/apt/sources.list
```

I started running the Update Manager the way you suggest however it didn't give the upgrade option so I read the directions. :) 

As for the sources.list here it is.

[COLOR="Blue"]# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
[/COLOR]

---

### Post by Rocket2DMn on 2008-03-02
Try removing the # at the front of the 3rd to last line (dapper-security main)
```
gksudo gedit /etc/apt/sources.list
```
Save and close, then update (this just refreshes the list, it doesn't download any updates):
```
sudo apt-get update
```
Then try the update manager again.
After that, I think I'm all out of ideas.

---

### Post by zvacet on 2008-03-02
If you try to upgrade from Dapper it will lead you to install Hardy and that is reason you gat that message.Hardy is not stable yet.If you want to upgrade to Edgy 


```
gksudo gedit /etc/apt/sources.list
```

change 
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
to 
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

click on search and select replace (or is it change I don´t know because I don´t use English version)>window will pop up and in **search** write** dapper** and above in replace type **edgy**.that should change your source list from Dapper to Edgy.See if it done correctly.If it is save and close.

```
  sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get dist-upgrade
```

```
sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a
```

---

### Post by TennTux on 2008-03-02
> **Rocket2DMn said:**
> Try removing the # at the front of the 3rd to last line (dapper-security main)
```
gksudo gedit /etc/apt/sources.list
```
Save and close, then update (this just refreshes the list, it doesn't download any updates):
```
sudo apt-get update
```
Then try the update manager again.
After that, I think I'm all out of ideas.

Tried uncommenting "dapper-security main", and it didn't work. Now I need to consider changing references to dapper to edgy.

---

### Post by Rocket2DMn on 2008-03-02
NOOO!  Do not do that, it is not safe to upgrade your system like that, you WILL screw it up.  You have to upgrade using the built-in methods or by doing a fresh install.  Simply changing Dapper to Edgy in your sources.list file will result in disaster.
I'm all out of ideas now, though I still think a fresh install is the best way to go (you can backup your /home directory and restore it after a fresh install as stated earlier).

---

### Post by TennTux on 2008-03-02
> **Rocket2DMn said:**
> NOOO!  Do not do that, it is not safe to upgrade your system like that, you WILL screw it up.  You have to upgrade using the built-in methods or by doing a fresh install.  Simply changing Dapper to Edgy in your sources.list file will result in disaster.
I'm all out of ideas now, though I still think a fresh install is the best way to go (you can backup your /home directory and restore it after a fresh install as stated earlier).

I was kind of feeling that changing Dapper to Edgy was a mistake however I was not getting any better suggestions.

I seem to remember in the recesses of my mind that I was given the option to upgrade at one point. Could I have clicked an option that said to not ask me again?

---

### Post by Rocket2DMn on 2008-03-02
It is entirely possible, try running
```
gksu update-manager --dist-upgrade
```

---

### Post by TennTux on 2008-03-02
> **Rocket2DMn said:**
> It is entirely possible, try running
```
gksu update-manager --dist-upgrade
```

Tried it. However... NG. Here is what I recieved.

> /usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
usage: update-manager [options]

update-manager: error: no such option: --dist-upgrade


I'm not entirely sure why I have python2.4 installed. I know I can check what a package depends on. Is there a way to see everything that's installed that depends on a package? I may be able to uninstall Python if that's the issue.

Note: I'm stepping out for an hour. Will continue at that point.

---

### Post by Rocket2DMn on 2008-03-02
You can try to uninstall python I guess, I don't know how to check the dependencies like that, you would probably have to use Synaptic of dpkg.

---

### Post by TennTux on 2008-03-02
Well. It doesn't look like uninstalling python is a realistic option. About 250 packages depend on python2.4 including a good portion of Gnome. At least that's what Synaptic says. Oh well.

---

### Post by Rocket2DMn on 2008-03-02
Sorry man, I'm out of ideas for you.  I really think a fresh install of Hardy when it is released is your best option.

---

### Post by zvacet on 2008-03-03
If you realy want to upgrade to Edgy download Edgy alternate CD and do upgrade with it.That is one of recommended options.See [here.](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by TennTux on 2008-03-03
Well, whatever the issue was it is no more. I did a fresh install of Gutsy.

Lost some data when I didn't notice that not all the stuff from my home dir was copied to the backup. I was paying so much attention to the hidden files that I didn't notice that none of my non-hidden directories where saved. And I'll spend the next week trying remember all the installed software and system file tweeks I made. I kept copies of the changed system files in one of the subdirs that didn't get saved. Cest Le Guerre

Anyway. Thanks for the effort

---

