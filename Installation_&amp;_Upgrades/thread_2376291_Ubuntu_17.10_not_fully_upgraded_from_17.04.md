---
title: "Ubuntu 17.10 not fully upgraded from 17.04"
date: 2017-11-01
forum: Installation &amp; Upgrades
---

### Post by carlo-sanguineti on 2017-11-01
Hi!

First of all, I must tell you I am not an Linux / Ubuntu expert.

Some days ago I upgraded my Ubuntu 17.04 to the new 17.10. It looks that the upgrade was not fully completed.

I have the same problem as in the thread [https://ubuntuforums.org/showthread.php?t=2375098](https://ubuntuforums.org/showthread.php?t=2375098) (Failure to download extra files), but it looks the problem is bigger.
- I was unable to install Italian on Settings -> Region & Language. I am Italian, Usually on PC I use English since I am an old man and when I started to work on PC English was the only language, so I got used to it, but sometimes I really need Italian too.
- My Unity Tweak Tool is not working properly, as I am unable to minimize a window just clicking on the related icon (at work I must use Windows and I am used to do this...)
- The System Monitor I installed looks quite weird after the update.

I know perfectly that some of my problems are not coming from Ubuntu properly, but I think - It maybe I'm wrong - that all these problem come from an incomplete upgrade. Is there anybody that tells me how to check if my 17.10 upgrade was fully completed or not?

Thank you very much in advance,

Carlo

---

### Post by #&amp;thj^% on 2017-11-01
Well we start by checking this:
```
lsb_release -a
```
Sorry paste back the output from the terminal.

---

### Post by carlo-sanguineti on 2017-11-01
Hi, thank you first.
I had this answer:

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

---

### Post by #&amp;thj^% on 2017-11-01
Looks like you got upgraded. :)
"Sometimes" you have to  remove or delete English to get Italiano then reinstall English.
If you can, try from a Gnome Session instead of Unity Session. (Log out of Unity>> Login as Gnome)

---

### Post by carlo-sanguineti on 2017-11-01
Sorry I really don't know to log out from Unity in a way that allow me to log in in Gnome :(
And I don't know what to do then...

---

### Post by #&amp;thj^% on 2017-11-01
Just to be clear for myself..can you give the output of this also.
```
echo $DESKTOP_SESSION
```

---

### Post by carlo-sanguineti on 2017-11-01
The answer is:

carlos@carlo-All-Series:~$ echo $DESKTOP_SESSION
ubuntu

---

### Post by #&amp;thj^% on 2017-11-01
Ok thanks.
Lets see if we can just use the terminal to get this installed then.
Run one line at a time:
```
cd /usr/share/locales
```
Now run this:
```
 ./install-language-pack it_IT
```
Followed by:
```
dpkg-reconfigure locales

```
That’s it! Repeat these steps for any other locale you need.

---

### Post by carlo-sanguineti on 2017-11-01
When I run ./install-language-pack it_IT it happens this:
sudo ./install-language-pack it_IT
[sudo] password for carlos: 
Generating locales (this might take a while)...
  it_IT.ISO-8859-1... done
Generation complete.
dpkg-trigger: error: must be called from a maintainer script (or with a --by-package option)


Type dpkg-trigger --help for help about this utility.

---

### Post by #&amp;thj^% on 2017-11-01
Humm? I'm not running Unity on 17.10
Try this way then:
```
 gnome-control-center region
```
Now see if you get the Italian Language!

---

### Post by carlo-sanguineti on 2017-11-01
Yes, thanks it looks I have now Italian Language. But I should have US English too..
when I run

gnome-control-center region

the answer is

(gnome-control-center:4203): common-cc-panel-WARNING **: Language en_US.UTF-8 not installed, trying to install it

... and I think it is not good.

The Region & Language settings window pops up. with both English and Italian language.
If I click on the manage installed language after selecting Italian, or English I see the Language support popup.

But now I have another problem. Google Chrome tells me on the top of his window (the header):

[ubuntu] Ubuntu 17.10 not fully up[graded from 17.04 - Google Chrome.

This appeared few minutes ago, just a new mushroom...

---

### Post by carlo-sanguineti on 2017-11-01
Yes, I see Italian language installed.

But I have two problems.

When I run

gnome-control-center region

I have this message:

(gnome-control-center:4203): common-cc-panel-WARNING **: Language en_US.UTF-8 not installed, trying to install it

And, suddendly, Google Chrome tells me on the header:

[ubuntu] Ubuntu 17.10 not fully upgraded from 17.04 - Google Chrome

SORRY, I POSTED TWICE THE SAME THING, EVEN WITH DIFFERENT WORDS. THE PAGE WAS NOT REFRESHING AND I THOUGHT I LOST MY POST.

---

### Post by carlo-sanguineti on 2017-11-01
I think my age makes me more stupid thav I was before:
I realized just now that the Google Chrome message is nothing else than the title of this thread...
Sorry

---

### Post by #&amp;thj^% on 2017-11-01
> **carlo-sanguineti said:**
> I think my age makes me more stupid thav I was before:

He he! I can relate to that myself. ;)
Show any errors from running this:
```
sudo apt full-upgrade
```

---

### Post by carlo-sanguineti on 2017-11-01
I did it. The very fast answer is:

carlos@carlo-All-Series:~$ sudo apt full-upgrade
[sudo] password for carlos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by #&amp;thj^% on 2017-11-01
Good! Looking good so far.;)
Now tell me what this has to report:
```
apt policy google-chrome-stable
```

---

### Post by carlo-sanguineti on 2017-11-01
the answer is:

google-chrome-stable:
  Installed: 54.0.2840.59-1
  Candidate: 54.0.2840.59-1
  Version table:
 *** 54.0.2840.59-1 100
        100 /var/lib/dpkg/status

---

### Post by carlo-sanguineti on 2017-11-04
Well, 1fallen, It looks that everything is working properly, now, with the exception of Unity Tweak Tools and System Load Indicator, that are noe Ubunti standard applications.

I thank you a lot for your patience and help.

Regards,

Carlo

---

