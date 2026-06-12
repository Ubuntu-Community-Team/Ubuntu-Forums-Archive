---
title: "Alient turns rpm files into a folder, not deb"
date: 2012-01-10
forum: Installation &amp; Upgrades
---

### Post by bobman321123 on 2012-01-10
When I try to convert an RPM file in ubuntu to a .deb file, it turns it into a group of folders instead. How do I get it to turn into the correct file?
Thanks,
Josh

---

### Post by raja.genupula on 2012-01-11
could you provide me the terminal code you entered . 

[http://code.google.com/p/foxoman/wiki/PackageConverter](http://code.google.com/p/foxoman/wiki/PackageConverter)

GUI way ^^^

---

### Post by bobman321123 on 2012-01-11
The code I entered was 
```
sudo alien packageName
```

---

### Post by bobman321123 on 2012-01-11
Also, I tried the GUI way, and it still converted it into urs, var, and opt folders.
Very frustrating....

---

### Post by satanselbow on 2012-01-11
Which version of Ubuntu are you using? There was a dodgey version of alien (8.83?) that had a few problems a while ago that never (from what I remember) got updated in the old repos.

The current version (oneiric repo) is 8.85

You can find your version by feeding alien the -V (capital letter) switch ;)

Also, Is it ANY rpm you convert or just one particular package?

also.. sorry posted before finished thinking ;)

Have you tried by explicitly stating the -d (to deb) ?

```
alien -d whatever.rpm
```

---

### Post by bobman321123 on 2012-01-11
I'm using Ubuntu 11.10. 
My alien version is 8.85.
I tried converting a whole folder of RPMs, and they all turned into folders.
Well, I tried specifying .deb in the GUI, but not in term. I'll give that a shot.

---

### Post by bobman321123 on 2012-01-11
I got an error message: 
```
chmod: invalid option -- '/'
Try `chmod --help' for more information.
mkdir: invalid option -- '/'
Try `mkdir --help' for more information.
mkdir -/debian failed:  at /usr/share/perl5/Alien/Package/Deb.pm line 299.
```

---

### Post by satanselbow on 2012-01-11
What was your exact command line for that? Try it on one test file for the time being ;)

---

### Post by bobman321123 on 2012-01-11
my exact command was ```

sudo alien -d maya2012_64.rpm
```

---

### Post by satanselbow on 2012-01-11
are you on a 64 bit OS?

what does ```
uname -a
``` have to say?

---

### Post by bobman321123 on 2012-01-11
Yes, I am on a 64 bit OS.
```
Linux josh-System-Product-Name 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by satanselbow on 2012-01-11
Maya pretty heavyweight software for alien to handle and alien has never claimed to be anything other than "experimental" software - I think  you might have just lucked out... someone else might come in with something useful but you are probably gonna have to look at installing it on an rpm based distro such as Fedora / CentOS :(

Sorry - really can't offer anymore help ;)

---

### Post by bobman321123 on 2012-01-11
Ack, well that sucks..... 
The weird thing is that it worked once, but it never worked after that.
*sigh* Just my luck

---

