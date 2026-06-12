---
title: "Unmet dependencies UCK"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by kestrel1 on 2014-12-30
Trying to use UCK to build a custom Ubuntu distro, but have hit a snag.
I select EN as the language and select the ISO image to use, UCK then does the first part of the build, but after trying to put the language files on I get an error, as follows:
```
The following packages have unmet dependencies:
 language-pack-touch-en : Conflicts: language-pack-en but 1:14.10+20141205 is to be installed
E: Unable to correct problems, you have held broken packages.
apt-get install language-pack-en language-pack-en-base language-pack-touch-en language-pack-gnome-en language-pack-gnome-en-base failed, error=100
```
The above is from the build.log file.
I have tried running 
```
apt-get install language-pack-en language-pack-en-base language-pack-touch-en language-pack-gnome-en language-pack-gnome-en-base
```
on the main distro & get the same problems. I then used aptitude. This appeared to help, as it said it would remove certain packages to help, but this didn't make any difference.
Has anyone else come across this?
I am using Ubuntu Gnome & the ISO I am using is Ubuntu Gnome as well.
Any help would be appreciated.
G

---

### Post by MAFoElffen on 2014-12-31
It says that language-pack-touch-en conflicts with language pack-en... but you then continued trying to reinstall the conflicting package. I'm trying to follow that logic-- Is there some reason why that I am not seeing? I'm thinking that they conflict with each other, so is one or the other, but not both... Meaning both cannot coexist. I'm thinking that language-pack-en-touch, includes verything the other has, plus...

Because if you removed language-pack-en, then there would be no conflict and then you could fix-broken on language-pack-touch-en, right? Such as:
```

sudo apt-get remove language-pack-en
sudo apt-get install -f
sudo apt-get install  language-pack-en-base language-pack-touch-en language-pack-gnome-en language-pack-gnome-en-base

```
Right? Either that, or you need to remove language-pack-en-touch... so have the other package language-pack-en... 
```

#alternate
sudo apt-get remove language-pack-en-touch
sudo apt-get install -f
sudo apt-get install  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base

```

But then again, you could just do:
```

sudo apt-get install -f

```
and see how it tries to resolve the conflict...

---

### Post by kestrel1 on 2014-12-31
OK, this is crazy.
I tried to remove both packages. With the language-pack-en I got an error saying it wasn't installed, so I thought 'OK I will remove the other one'
When trying to remove language-pack-en-touch I got an error that it couldn't be found. 
I then tried
```
sudo apt-get install  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
```
This actually said it was removing the language-pack-touch-en (yes I have now noticed that I was trying to remove a pack that didnt exist en-touch)
Anyway, I thought that might have sorted it, but when trying to go through UCK I get the same error.
I have a plan, so will update once I have tried it.

---

### Post by kestrel1 on 2014-12-31
OK, I have got past this now.
Obviously UCK is taking these files from the ISO image & it must be built in to the ISO I was using. I used the Ubuntu 14.10 ISO and it went through OK.
Thanks for your help.

---

### Post by fingerheroes on 2015-10-07
The answer is to bypass the first language prompt. Don't check ANYTHING on it. Then, check the language for the next two.

If that doesn't work, skip both the first AND second language prompts, and just do the third one.

---

