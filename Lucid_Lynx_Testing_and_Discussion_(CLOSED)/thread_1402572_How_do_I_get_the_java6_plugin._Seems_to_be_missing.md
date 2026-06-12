---
title: "How do I get the java6 plugin. Seems to be missing in the repos."
date: 2010-02-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-02-09
sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

sun-java6-bin:
Package sun-java6-bin has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by zika on 2010-02-09
Try here: [http://ubuntuforums.org/showthread.php?t=1381226](http://ubuntuforums.org/showthread.php?t=1381226)
After reinstall I'm back to the jre downloaded from: [http://ubuntuforums.org/showthread.php?t=1381226](http://ubuntuforums.org/showthread.php?t=1381226)
If You need instructions: Just unpack it in some chosen folder. Sym-link libnpjp2.so in ~/.mozilla/plugins to that file in /chosen_folder/jre1.6.0_18/lib/amd64/libnpjp2.so and that is it.
That is for 64-bit java...
For 32-bit use Synaptic.
If unexperienced, use the first method (ppa and .deb)...
[ ]("http://ubuntuforums.org/showthread.php?t=1381226")

---

### Post by ronacc on 2010-02-09
the JRE is in synaptic , sun-java6-jre

---

### Post by philinux on 2010-02-09
> **ronacc said:**
> the JRE is in synaptic , sun-java6-jre

Not anymore lol

sun-java6-jre:

Package sun-java6-jre has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list


Also the sun-java6-plugin is not even listed.

---

### Post by thiebaude on 2010-02-09
I dont know if you have to enable 3rd party repositories, for the java to be in synaptic.

---

### Post by philinux on 2010-02-09
> **thiebaude said:**
> I dont know if you have to enable 3rd party repositories, for the java to be in synaptic.

Notice the plugin is not listed.

---

### Post by ronacc on 2010-02-09
I see now , the only reason it shows for me is that I already have it installed .

---

### Post by philinux on 2010-02-09
> **ronacc said:**
> I see now , the only reason it shows for me is that I already have it installed .

I went to a site that needs the java plugin and found it not working. Had a look in about plugins and saw that it was missing.

I tried to reinstall sun-java6-plugin but synaptic had the option unavailable.

So I uninstalled the plugin thinking I'd then reinstall it and it vanished. :p

---

### Post by ronacc on 2010-02-09
On first boot after a fresh install there is a big bunch of things I install , during a dev cycle I also set my apt-cache not to delete ANYTHING incase I need to revert to an earlier package .

---

### Post by philinux on 2010-02-09
Any thoughts on why the three packages aren't available anymore?

---

### Post by ronacc on 2010-02-09
who knows why they do anything , maybe the decided to push icedtea real hard .

---

### Post by jppr on 2010-02-09
java sun-6 is gone :wink: and, icedtea6 and openjdk-6  is coming. repos and packages change and is good sometimes to do a clean / fresh installation

---

### Post by philinux on 2010-02-09
> **jppr said:**
> java sun-6 is gone :wink: and, icedtea6 and openjdk-6  is coming. repos and packages change and is good sometimes to do a clean / fresh installation

Thanks for that I'll install icedtea for now then.

I know java6 was installed with my alpha2 clean install. I only noticed today that the plugin had gone when I tried to use a site that uses java. ;)


Found this.

Change log for &#8220;sun-java6&#8221; package in Ubuntu

   1. Ubuntu
   2. &#8220;sun-java6&#8221; package
   3. Change log

6-16-1
Deleted in lucid-release on 2010-01-29 (Reason: unmaintained, superseded by OpenJDK in main)

---

### Post by OrangeCrate on 2010-02-09
> **jppr said:**
> java sun-6 is gone :wink: and, icedtea6 and openjdk-6  is coming. repos and packages change and is good sometimes to do a clean / fresh installation

I confirm that a fresh install of Alpha 2 loads openjdk through the restricted extras package.

---

### Post by ronacc on 2010-02-09
thats great as long as icedtea actually works EVERYWHERE that sun java does , it hasn't in the past .

---

### Post by OrangeCrate on 2010-02-09
> **ronacc said:**
> thats great as long as icedtea actually works EVERYWHERE that sun java does , it hasn't in the past .

This install has been on here for a week or so, and I haven't had any hiccups so far...

---

### Post by drs305 on 2010-02-09
If you simply *must* have Sun's java:

```
sudo add-apt repository ppa:portis25/test
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

Of course, the purpose of Alpha/Beta testing is to provide feedback on the proposed OS. Giving *openjdk* a chance and reporting what doesn't work is probably in all our best interest.

---

### Post by ranch hand on 2010-02-09
I wonder if the switch has to do with problems upgrading from 8.04 or if the switch was responsible for some very tough problems in getting the upgrade to work.

---

### Post by ronacc on 2010-02-09
> **drs305 said:**
> If you simply *must* have Sun's java:

```
sudo add-apt repository ppa:portis25/test
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

Of course, the purpose of Alpha/Beta testing is to provide feedback on the proposed OS. Giving *openjdk* a chance and reporting what doesn't work is probably in all our best interest.

I test it the way I am actually going to use it since that is what is meaningful to me .

---

### Post by SevenMachines on 2010-02-10
remember, openjdk is sun's effort to open-source java (last i recall it was sun's engineers that vetted all incoming patches before acceptance :( ). since last year it passed all of their 'official java implementation' compliance tests. Thats why sun java6 is deprecated for openjdk. I'm not sure what encumbered code from 3rd parties is left to be implemented, last i checked over a year ago is was officially <1%, it may be less or zero now. 
Official sun java compliance wise, openjdk IS java6, if theres problems then these are bugs (in openjdk libraries, or in the java program that fails) that need to be fixed!

---

### Post by Rallg on 2010-02-10
@SevenMachines: Thanks for that clarification. I don't use Java much but had Sun Java installed (until lucid removed it). I wasn't going to bother with openjdk until you clarified what it was.

---

### Post by zika on 2010-02-10
Just to reiterate, I'm using jre1.6.0_18 as 64-bit-plugin... If there is need for instructions on how to do that, just ask.

---

### Post by Zorael on 2010-02-12
As far as I understand the "new plugin" of OpenJDK/IcedTea isn't written yet, so to view Java applets in Chromium (which only supports the new plugin format) you'd have to use Sun's - of which there aren't any packages. I'll try the ppa.

---

### Post by Riverside on 2010-02-12
If a decision has been taken not to include sun-java packages in 10.4, that is disappointing.  To the best of my knowledge clients using non-Sun java implementations will be unable to install the Network Connect component of Juniper SSL VPN solutions which are widely deployed at corporate sites.

---

### Post by cosimo on 2010-03-01
Hey guys..
i believe, in fact, that there will be a partner repo for sun-java.
Also..openjdk is useless for most applications that need sun java and many sites that require sun java.
Icedtea has never worked properly.
I am not interested in openjdk and have no interest in reporting bugs etc.
 having said that.. let me explain a bit;
I have many clients that require certain java applications to run their business...one such application is  OpenBravo...a POS .
  I cant go to them and say you cant upgrade to Lucid because there is no sun java available, when they "insist" on clean installs of current ubuntu releases!
 I think it's a great idea to have an open source java however I have no issues with sun java and believe it should be the default
  It can be installed manually also.
in my case...no sun java means no ubuntu for my clients !
Also openjdk will not go over well on production machines. at least at this point and which has lasted for quite a long time.
   I thnks its great to do open java however,,, like the nouveau  open nvidia driver ..it is too soon  and way not ready!

coz

---

### Post by Keyper7 on 2010-03-02
> **Zorael said:**
> As far as I understand the "new plugin" of OpenJDK/IcedTea isn't written yet, so to view Java applets in Chromium (which only supports the new plugin format) you'd have to use Sun's - of which there aren't any packages. I'll try the ppa.

What exactly to you mean by "isn't written yet?"

[http://packages.ubuntu.com/lucid/icedtea6-plugin](http://packages.ubuntu.com/lucid/icedtea6-plugin)

> **cosimo said:**
> (...) Also..openjdk is useless for most applications that need sun java and many sites that require sun java. Icedtea has never worked properly. (...) Also openjdk will not go over well on production machines.

Are your statements based on the current version, or at least any version released since OpenJDK passed the Technology Compatibility Kit? Because passing the TCK means full compatibility. Not according to the OpenJDK developers, but according to Sun itself.

---

### Post by zika on 2010-03-02
IcedTea6-plugin is 64-bit on 64-bit install...?

---

### Post by Reiger on 2010-03-02
Seems so, from glancing at the dependencies and the fact there are 2 architecture flavours(i386 and amd64).

---

### Post by Keyper7 on 2010-03-02
> **zika said:**
> IcedTea6-plugin is 64-bit on 64-bit install...?

It already was, much before Sun released a 64-bit version. :)

---

### Post by Zorael on 2010-03-02
> **Keyper7 said:**
> What exactly to you mean by "isn't written yet?"

[http://packages.ubuntu.com/lucid/icedtea6-plugin](http://packages.ubuntu.com/lucid/icedtea6-plugin)
Key word, **new** plugin.
> What is the New Java Plug-in?

This is a new implementation of the Java Plug-In that features increased reliability, ability to specify large heap sizes, ability to select a specific JRE version to execute a particular applet, and support for signed applets on Windows Vista.

What are the web browsers supported by the New Java Plug-in?

The New Plug-in is designed to work with:
Internet Explorer 6 and 7 on Windows XP and Windows Vista
Firefox 3 pre-release builds on Windows XP, Windows Vista, Solaris and Linux
Note: The new Plug-in does not work with Firefox 2, and no support is planned for this browser with the New Plug-in.
[http://java.sun.com/javase/6/6u10faq.jsp#NewPlugIn](http://java.sun.com/javase/6/6u10faq.jsp#NewPlugIn)

Whenever you see a reference to "NPPlugin" or "libnp*" Java libraries, that's the new plugin.

---

### Post by raggari on 2010-03-02
> **Keyper7 said:**
> What exactly to you mean by "isn't written yet?"

[http://packages.ubuntu.com/lucid/icedtea6-plugin](http://packages.ubuntu.com/lucid/icedtea6-plugin)



Are your statements based on the current version, or at least any version released since OpenJDK passed the Technology Compatibility Kit? Because passing the TCK means full compatibility. Not according to the OpenJDK developers, but according to Sun itself.

Icedtea-plugin is not part of the OpenJDK. That's the reason why it's not called openjdk-plugin. It's not part of passed TCK.

---

### Post by Keyper7 on 2010-03-02
> **Zorael said:**
> Key word, **new** plugin.

[http://java.sun.com/javase/6/6u10faq.jsp#NewPlugIn](http://java.sun.com/javase/6/6u10faq.jsp#NewPlugIn)

Whenever you see a reference to "NPPlugin" or "libnp*" Java libraries, that's the new plugin.

Now that is a poorly chosen name. Thanks for the clarification.

---

### Post by ViperScull on 2010-03-02
Testing OpenJDK.

JDownloader works much worse. Much slower, particularly when it's downloading.
The lack of sun fonts is a con as well.

---

### Post by rogerdean on 2010-03-02
Zotero citation manager Firefox addon doesn't work with OpenJDK. This is a must for many students, researchers and others. Discussion here...

[http://forums.zotero.org/discussion/11429/zotero-in-ubuntu-104-lucid-lynx/#Item_6](http://forums.zotero.org/discussion/11429/zotero-in-ubuntu-104-lucid-lynx/#Item_6)

---

### Post by rogerdean on 2010-03-02
they say sun-java6 has now been published in the partner repository. can't see it yet myself...

[https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.18-2](https://launchpad.net/ubuntu/lucid/+source/sun-java6/6.18-2)

---

### Post by rogerdean on 2010-03-02
it's there now, in the partner repos. many thanks to whoever did this :-)

---

### Post by rogerdean on 2010-03-02
folks, i've installed sun-java6-bin sun-java6-jre and sun-java6-plugin from the partner repository. but in my firefox plugins panel i only have the icedtea npr plugin, no sun java. 

did something go wrong? are there other steps i need to get sun java into my firefox?

cheers!
Roger

---

### Post by philinux on 2010-03-02
> **rogerdean said:**
> folks, i've installed sun-java6-bin sun-java6-jre and sun-java6-plugin from the partner repository. but in my firefox plugins panel i only have the icedtea npr plugin, no sun java. 

did something go wrong? are there other steps i need to get sun java into my firefox?

cheers!
Roger

```
sudo update-alternatives --config java 
```

---

### Post by Keyper7 on 2010-03-02
edit: philinux beat me to it

---

### Post by rogerdean on 2010-03-02
keyper7, please put your suggestion back! phil's didn't get the plugin into firefox, but yours might!
cheers :-)

---

### Post by crjackson on 2010-03-02
Just follow the JAVA section from this page.  This is my blog and I have it running on my Lucid and Karmic machines (several) from this procedure.

[http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html](http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html)

---

### Post by rogerdean on 2010-03-02
brilliant crjackson, that got it! the exact command i needed was -

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.18/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
```

many thanks to all for helping out

cheers
roger

---

### Post by crjackson on 2010-03-02
> **rogerdean said:**
> brilliant crjackson, that got it! the exact command i needed was -

```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.18/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
```

many thanks to all for helping out

cheers
roger

Glad it helped ;)

I tend to keep the link pointing to the original folder name.

---

### Post by philinux on 2010-03-02
> **crjackson said:**
> Just follow the JAVA section from this page.  This is my blog and I have it running on my Lucid and Karmic machines (several) from this procedure.

[http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html](http://buck-nasty.blogspot.com/2010/02/installing-firefox-36-and-java-618.html)

Does this work for 64 bit?

---

### Post by donniezazen on 2010-03-02
Latest update has added Java package to the repository.

---

### Post by Uncle Spellbinder on 2010-03-02
32 bit: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-)

64 bit: [http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-64-bit-)

Worked flawlessly for me in Karmic and equally  so in Lucid Alpha 3.

---

### Post by CoreyB. on 2010-03-03
> **soham_1207 said:**
> Latest update has added Java package to the repository.

Yeah, it's in the partner repos.

[Index of /dists/lucid/partner]("http://archive.canonical.com/dists/lucid/partner/")

---

### Post by crjackson on 2010-03-03
> **philinux said:**
> Does this work for 64 bit?

I haven't tried it but it should work.

---

### Post by scaine on 2010-03-03
> **crjackson said:**
> I haven't tried it but it should work.

Working on 64 bit install here.  I had to change the command (from post 42) slightly because it had an i386 directory which doesn't exist on a 64-bit install.

So I used (obviously, but I'll show it anyway) :
```
sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.18/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/
```

Without that command, Firefox will continue to launch OpenJDK as its plug-in, instead of Sun JRE.  Despite the update-alternatives command appearing to work okay.

OpenJDK does not launch the Facebook Photo Uploader.  Can someone advise on the best method to file a bug against it?  It works fine with the Sun JRE.

---

### Post by ViperScull on 2010-03-03
> **scaine said:**
> 
OpenJDK does not launch the Facebook Photo Uploader.  Can someone advise on the best method to file a bug against it?  It works fine with the Sun JRE.

If you push "Try the simple uploader" (down the Cancel button) you will be able to upload them.

---

### Post by ViperScull on 2010-03-03
> **scaine said:**
> 
OpenJDK does not launch the Facebook Photo Uploader.  Can someone advise on the best method to file a bug against it?  It works fine with the Sun JRE.

If you click "Try the simple uploader" (down the Cancel button) you will be able to upload them.

anyway, to report it, you can try [here]("http://openjdk.java.net/groups/web/bugzilla.html")

---

### Post by lusu777 on 2010-04-05
They just added the java sun packages u can now install them by using synaptic :D

---

### Post by zika on 2010-04-06
Or, simply```
sudo add-apt-repository ppa:voronov84/andreyv
```and You'll have Flash and Java up-to-date. Great ppa! Thank YouAndrey Veronov!

---

