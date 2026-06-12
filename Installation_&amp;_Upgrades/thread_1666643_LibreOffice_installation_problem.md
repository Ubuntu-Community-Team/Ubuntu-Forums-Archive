---
title: "LibreOffice installation problem"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by sdmike6 on 2011-01-14
I'm following [THIS]("http://drupal.txwikinger.me.uk/content/libreoffice-now-available-ppa-ubuntu-1010-and-1004") tutorial on how to remove OpenOffice and then install LibreOffice but I ran into a problem at the end of the article.

I'm on this part:
> As explained in a comment below, in order to install the spellchecker  the following line needs to be used (with adjustment of the locale (the  example uses English-US):

sudo apt-get install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us

When I execute the last command I get an error and I know it's because it wants me to install another file but I'm not sure which one.

```
user@computer:~$ sudo apt-get install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
Reading package lists... Done
Building dependency tree       
Reading state information... Done
aspell is already the newest version.
aspell-en is already the newest version.
aspell-en set to manually installed.
dictionaries-common is already the newest version.
dictionaries-common set to manually installed.
hunspell-en-us is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 hunspell-en-us : Conflicts: myspell-en-us but 1:3.2.1-2ubuntu1 is to be installed
E: Broken packages

```

What should I do?

---

### Post by sikander3786 on 2011-01-15
Try using aptitude. It solves pacakge dependecy problems like this.

```
sudo aptitude install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
```

---

### Post by sdmike6 on 2011-01-16
> **sikander3786 said:**
> Try using aptitude. It solves pacakge dependecy problems like this.

```
sudo aptitude install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
```

Wow thanks for the advice, it worked like a charm.

---

### Post by sdmike6 on 2011-01-16
> **sikander3786 said:**
> Try using aptitude. It solves pacakge dependecy problems like this.

```
sudo aptitude install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
```

Wow thanks for the advice, it worked like a charm.

---

### Post by sdmike6 on 2011-01-16
> **sikander3786 said:**
> Try using aptitude. It solves pacakge dependecy problems like this.

```
sudo aptitude install aspell aspell-en dictionaries-common hunspell-en-us myspell-en-us
```

Wow this is good to know and it solved my problem.

Thank You :)

---

### Post by Guegs on 2011-01-16
Didn't work for me.

```
sudo: aptitude: command not found
```

---

### Post by sikander3786 on 2011-01-19
> **Guegs said:**
> Didn't work for me.

```
sudo: aptitude: command not found
```
Welcome to the forums :-)

It means you are using Maverick which doesn't come with aptitude by default. You need to install aptitude prior to using it for installation of other packages.

Search Software Center or Synaptic for 'aptitude' package, install it and then follow the above mentioned command.

---

