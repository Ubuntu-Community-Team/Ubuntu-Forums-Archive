---
title: "Can't install gstreamer0.8-lame"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by James_Black on 2005-05-31
I'm training to install gstreamer0.8-lame, like explained on the unofficial Ubuntu starters guide site. When I do this, I get this message:

```
 $ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gstreamer0.8-lame: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
E: Broken packages

```

So what is wrong? This is what I have in my sources.list:

```
## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

# Backports
#deb http://backports.ubuntuforums.org/ubp hoary-backports main universe multiverse restricted
#deb http://backports.ubuntuforums.org/ubp hoary-extras main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp hoary-backports main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp hoary-extras main universe multiverse restricted


```

---

### Post by veratyr on 2005-06-01
Having this same problem with libc6.

---

### Post by basementjack on 2005-06-01
[QUOTE=James_Black]I'm training to install gstreamer0.8-lame, like explained on the unofficial Ubuntu starters guide site. When I do this, I get this message:

...
So what is wrong? This is what I have in my sources.list:

[/QUOTE]

Did you remember to do a,

```
sudo apt-get update
``` 

?

---

### Post by veratyr on 2005-06-01
I got it to work. Try commenting out these in your sources.list

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by James_Black on 2005-06-01
[QUOTE=basementjack]Did you remember to do a,

```
sudo apt-get update
``` 

?[/QUOTE]


Yes, I did, but no luck. :(


[QUOTE=veratyr]I got it to work. Try commenting out these in your sources.list

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main[/QUOTE]

That's very odd. I already have that in my sources.list, and it ain't working.  :???:

---

### Post by veratyr on 2005-06-01
Do you mean you have them commented or uncommented? When i had them uncommented it did not work. As soon as I commented them back out and did a sudo apt-get update it installed fine. So in your sources.list it would look like:

## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by Alexander Kirillov on 2005-06-01
[QUOTE=veratyr]Do you mean you have them commented or uncommented? When i had them uncommented it did not work. As soon as I commented them back out and did a sudo apt-get update it installed fine. So in your sources.list it would look like:

## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
## deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main[/QUOTE]
 There is a version of gstreamer-lame in marillat (this is the one which can not be installed becuase of dependency problems) and in backports (this one can be installed). So when you comment marillat repos, the one from backports is used.

---

### Post by James_Black on 2005-06-02
Thanks guys! I was able to install it now!  \\:D/

---

