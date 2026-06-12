---
title: "How to select Php in Many Flavours?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by jaya28inside on 2010-09-02
I thought I should move on to packaging and compiling section.
But, Before that I hope this topic covered first.

I realized that apt-get update, upgrade and install
from my Ubuntu Linux (Server) would eventually going to its
main repository which is taking php5.3

My question here is how to obtain the php non 5.3?

I tried to search and work arround.
Several cases I found, and yes it help me alot.
Is to change the repository to karmic, and make a php file containing packages detail stored at /etc/apt/preferences.d

But then, once I done that. What I got is php 5.2.10
My objective of course already met. But here, how to make it specifically made by ourself?

Perhaps there's a lot of Php version on the php.net
but they just publish the source, which means I need to recompile it, and install first its dependencies correctly.

I found out this link
> 
[http://www.phpbuilder.com/manual/install.unix.debian.php](http://www.phpbuilder.com/manual/install.unix.debian.php)


but it didnt mention how to select the Flavour of Php 5.x.x
it just get the latest Php. I may not need the latest php for a moment,...

hmmm, so, let's get back to the main question above. 
is there Anyone have ever done this?

;) mind to share with us....?

---

### Post by VcDeveloper on 2010-09-02
This is some what I need to know myself.  I'm about to install the LAMP server and I need the php5.2.x for Drupal 6.xx.  Drupal 6.xx can not function properly on php5.3.x.  Still waiting for Drupal 7 production release!  Any help on this?

---

### Post by VcDeveloper on 2010-09-02
> **VcDeveloper said:**
> This is some what I need to know myself.  I'm about to install the LAMP server and I need the php5.2.x for Drupal 6.xx.  Drupal 6.xx can not function properly on php5.3.x.  Still waiting for Drupal 7 production release!  Any help on this?

I read this post [http://ubuntuforums.org/showthread.php?t=1447401&highlight=reverting+php5.2+lucid](http://ubuntuforums.org/showthread.php?t=1447401&highlight=reverting+php5.2+lucid) and I followed the direction, But what install program do you use?  I ran the Synaptic Package Manager and didn't see any changes.

---

### Post by jaya28inside on 2010-09-02
dear VcDeveloper,

I suppose what you'll get after installing the
LAMP server of course you'll get the latest PHP version
at the time you're installing it. Perhaps 
it make me more confident that you'll get php 5.3 if you're connected through internet. (apt-get update).

basically, we do installing through executing command 

> 
sudo apt-get install ThingYouWanted


anyway If you done already installing LAMP Server,(it's okay).
But you need to do something more. 
i suggest now you do downgrading. 
Similar case I experienced this morning.
I done with that already.

But before that. let me ask you first, whether your ubuntu is capable to access internet or not?
if yes, then using apt-get command would not be a problem.
again, before doing apt-get you need to switch repository to karmic. From there I got php 5.2 for a real. But it's 5.2.10 not 5.2.14 or other that i wanted. 

are you in this way? :o

---

### Post by VcDeveloper on 2010-09-02
> **jaya28inside said:**
> 

But before that. let me ask you first, whether your ubuntu is capable to access internet or not?



Yes, my Ubuntu can access the internet, I was waiting for a reply before I start installing hoping I can get the 5.2.x, but if I understand you right, i need to install the LAMP first and then down grade?

> **jaya28inside said:**
> 

before doing apt-get you need to switch repository to karmic. 



Do I do this before I install the LAMP or After and how do I switch repos to karmic?

> **jaya28inside said:**
> 

From there I got php 5.2 for a real. But it's 5.2.10 not 5.2.14 or other  that i wanted. 
 


The 5.2.10 is what I need.

---

### Post by jaya28inside on 2010-09-02
Yes, You may do LAMP installation until complete.

After you did install the LAMP, next thing you need to do is downgrading the php. because at the time LAMP installed, you may get the higher version from php 5.2, which is php 5.3. I got that one previously.

Ok.

To do downgrading php from 5.3 to 5.2,
change the repository. Make sure there's php 5.3 installed first. :D
I just done for it yesterday. Yes, php 5.2.10 is the version which you will get after doing downgrading from php 5.3 (i'm sure).

Here i give you a thread for doing downgrading from php 5.3 to php 5.2.
Check it out! 
> 
[http://ubuntuforums.org/showthread.php?p=9799311](http://ubuntuforums.org/showthread.php?p=9799311)


---

### Post by VcDeveloper on 2010-09-02
> **jaya28inside said:**
> 
Here i give you a thread for doing downgrading from php 5.3 to php 5.2.
Check it out!

I ran the script but it didn't install the 5.2.10... it just removed the php5.3.x installation..., I checked Synaptic Package Manager and php5.3.x is there...

Any suggesting?

---

### Post by VcDeveloper on 2010-09-03
I just rent back to 9.10 and locked php5.2.10 then upgrade to 10.04...

---

### Post by jaya28inside on 2010-09-09
ah? not working ? 
very-very strange... what's the error code given anyway?
I did it okay here...

---

### Post by slakkie on 2010-09-09
It is pretty easy.

1) Enable the karmic repositories.

```

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ karmic-updates main restricted universe multiverse

```

2) Update the package list
```

sudo aptitude update

```

3) Make sure you stay on php5.2.x by editting /etc/apt/preferences

```

sudo vi /etc/apt/preferences

```

```

Package: php5
Pin: version 5.2.*
Pin-Priority: 1001

```

4) Install the correct package
```

sudo aptitude install php5
# or:
sudo aptitude install php5/karmic
# or:
sudo aptitude install php5/karmic-updates

```

Done.

Ps. Also have a look at other php5 packages you have installed, eg:

```

$dpkg -l | grep php5
ii  libapache2-mod-php5                        5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting language (Apache 2 module)
ii  php5                                       5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                                   5.3.2-1ubuntu4.2                                command-line interpreter for the php5 scripting language
ii  php5-common                                5.3.2-1ubuntu4.2                                Common files for packages built from the php5 source
ii  php5-gd                                    5.3.2-1ubuntu4.2                                GD module for php5
ii  php5-mysql                                 5.3.2-1ubuntu4.2                                MySQL module for php5

```

You might want to rinse/repeat the procedure with these packages :)

You can add this to /etc/apt/preferences:

```

Package: php5 libapache2-mod-php5 php5-cli php5-common php5-gd php5-mysql
Pin: version 5.2.*
Pin-Priority: 1001

```

And then run:

```

sudo aptitude install php5 libapache2-mod-php5 php5-cli php5-common php5-gd php5-mysql

```

That should cover all your php5 packages :)

---

### Post by VcDeveloper on 2010-09-10
> **slakkie said:**
> That should cover all your php5 packages :)

Cool! I shall give it a try!  

......................by the way, going back to 9.10 Karmic didn't work, any comments on that will I'm running the above?

---

### Post by VcDeveloper on 2010-09-10
> **jaya28inside said:**
> ah? not working ? 
very-very strange... what's the error code given anyway?
I did it okay here...

Everything run smoothly and didn't get an error code...

---

### Post by slakkie on 2010-09-10
> **VcDeveloper said:**
> Cool! I shall give it a try!  

......................by the way, going back to 9.10 Karmic didn't work, any comments on that will I'm running the above?

?? You shouldn't downgrade all your packages, just the PHP5 packages.

Or I don't understand your question.

You can check the php version by running php --version (or something similiar. phpinfo() will also do the trick :)

---

### Post by VcDeveloper on 2010-09-10
[QUOTE=slakkie;9828079]?? You shouldn't downgrade all your packages, just the PHP5 packages.

Or I don't understand your question.

/QUOTE]

I was just mentioning when I went back to 9.10 karmic and tried to do a "lock version" on the php5.2.10, then upgrade back to 10.04 LTS it didn't work.  And wanted any comments as to why it still upgraded the "lock version"....

---

### Post by slakkie on 2010-09-10
I should test this in a VM. I cannot answer your question atm.

---

### Post by VcDeveloper on 2010-09-10
> **slakkie said:**
> 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse


I have a /etc/apt/sources.list.d/karmic.list containing:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

......and it has varies combination of what you have listed, do I need to replace this file with just your list or leave it as is?  This was already here.

> **slakkie said:**
>  
Make sure you stay on php5.2.x by editting /etc/apt/preferences

sudo vi /etc/apt/preferences
Package: php5
Pin: version 5.2.*
Pin-Priority: 1001


Do I put a file name perferences in the /etc/apt folder, because I have a folder called /etc/apt/preferences.d and do I put the file in here?

> **slakkie said:**
> 
Ps. Also have a look at other php5 packages you have installed, eg:

$dpkg -l | grep php5
ii  libapache2-mod-php5                        5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting language (Apache 2 module)
ii  php5                                       5.3.2-1ubuntu4.2                                server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                                   5.3.2-1ubuntu4.2                                command-line interpreter for the php5 scripting language
ii  php5-common                                5.3.2-1ubuntu4.2                                Common files for packages built from the php5 source
ii  php5-gd                                    5.3.2-1ubuntu4.2                                GD module for php5
ii  php5-mysql                                 5.3.2-1ubuntu4.2                                MySQL module for php5

You might want to rinse/repeat the procedure with these packages :)

You can add this to /etc/apt/preferences:

Package: php5 libapache2-mod-php5 php5-cli php5-common php5-gd php5-mysql
Pin: version 5.2.*
Pin-Priority: 1001
And then run:

sudo aptitude install php5 libapache2-mod-php5 php5-cli php5-common php5-gd php5-mysql

That should cover all your php5 packages :)

Will this replace the 5.3.2 or will both version be available to select from?

---

### Post by slakkie on 2010-09-12
> **VcDeveloper said:**
> I have a /etc/apt/sources.list.d/karmic.list containing:
......and it has varies combination of what you have listed, do I need to replace this file with just your list or leave it as is?  This was already here.


You have the correct karmic sources.list, so you don't need to edit it. 

> 
Do I put a file name perferences in the /etc/apt folder, because I have a folder called /etc/apt/preferences.d and do I put the file in here?


Yes, create the /etc/apt/preferences file, it is a similar concept as /etc/apt/sources.list and /etc/apt/sources.list.d.

> 
Will this replace the 5.3.2 or will both version be available to select from?

It will replace 5.3.2, you can still opt for 5.3.2, but you will need to change the preferences file in order to keep 5.3.2. The 1001 Pin-Priority will force 5.2.x. To have 5.3.2 just remove the lines, issue an php5 install command and then it will install 5.3.2 (or whatever candidate is higher - you can see that by running apt-cache policy php5).

---

### Post by madjoe on 2010-12-09
I have successfully downgraded my PHP to 5.2.10, but now I have further questions:

1) I ran the following command line "dpkg -l | grep php5" and this is the output:
```
ii  libapache2-mod-php5                  5.2.10.dfsg.1-2ubuntu6.5                          server-side, HTML-embedded scripting language (Apache 2 module)
ii  php5                                 5.2.10.dfsg.1-2ubuntu6.5                          server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                             5.2.10.dfsg.1-2ubuntu6.5                          command-line interpreter for the php5 scripting language
ii  php5-common                          5.2.10.dfsg.1-2ubuntu6.5                          Common files for packages built from the php5 source
ii  php5-gd                              5.2.10.dfsg.1-2ubuntu6.5                          GD module for php5
rc  php5-imagick                         3.0.0~rc1-1build1                                 ImageMagick module for php5
rc  php5-mcrypt                          5.3.3-0ubuntu2                                    MCrypt module for php5
ii  php5-mysql                           5.2.10.dfsg.1-2ubuntu6.5                          MySQL module for php5
```

Are those packages **php5-mcrypt** and **php5-imagick** ok for my downgraded php version?

2) I guess I shouldn't mess with replacing the PHP 5.2.10 with PHP 5.2.14 manually and maybe I should just wait to be added in repos, isn't it?

---

