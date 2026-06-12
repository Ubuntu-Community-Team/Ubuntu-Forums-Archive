---
title: "Firefox 18.0 update lost local language"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by fvilaubi on 2013-01-10
Ubuntu 12.10 64bits. Yesterday periodical update, goes from Firefox 17.0 to 18.0.

I am using firefox 17 in Catalan language and I get "you must reinicialize the browser" message.

After Firefox reinitilization I lost locale language setting. 
In firefox About:config I have in "general.useragent.locale" en-US. I changed to "ca" (my locale)

In "tools > add-ons > languages" there is NO catalan language pack!

but Ubuntu software center, and "system parameters > langage support" are installed catalan preference. 

How can I get my locale with Firefox 18?

---

### Post by dino99 on 2013-01-10
sudo apt-get install firefox-locale-ca

---

### Post by fvilaubi on 2013-01-10
I am up to date. Look the apt-get reply of your command:
> francesc@Pccesc:~$ sudo apt-get install firefox-locale-ca
S'està llegint la llista de paquets… Fet 0%
S'està construint l'arbre de dependències       
S'està llegint la informació de l'estat… Fet%
firefox-locale-ca ja es troba en la versió més recent.
0 actualitzats, 0 nous a insta&#320;lar, 0 a suprimir i 0 no actualitzats.
francesc@Pccesc:~$

Translated to english is:
firefox-locale-ca is up to date. 
0 updatet, 0 new, 0 deleted and 0 not updated.


I do the same with GUI in Ubuntu software center, search for "firefox" and click on the link "show 218 technical items", one of this items is "Catalan language package" and is green checked!

Why in "tools > add-ons > languages" there is NO Catalan language pack?

and this is perfect working with firefox 17.0, few minutes before update to 18.0! I am using firefox and updating Ubuntu, and I get the "you must reinitialize firefox" message. After reinitializing all menus are in English!

NOTE: If I write a text in Catalan, this text is correct Catalan checked and i get good substitution Catalan words. (pop-up window wit spell checker in languages button, gives my Catalan availability and works well)

---

### Post by arakelov on 2013-01-10
I'm experiencing the same issue. Seems that firefox-locale-ca has some problem.

Thanks.

---

### Post by Bufeu on 2013-01-10
Tested this in VirtualBox and this seems to affect both 12.04 and 12.10. Bug reported: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098296](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098296).

EDIT: New bug, this time reported using Apport: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312). Please, mark the two bugs as "Yes, this affects me" to make a fix come so fast as possible.

---

### Post by forkandles on 2013-01-10
fvilaubi,

Would using an alternative browser and the information below help you, pending solution of the Firefox bug?

[http://askubuntu.com/questions/95190/what-is-an-ubuntu-localized-image-and-how-do-i-create-one](http://askubuntu.com/questions/95190/what-is-an-ubuntu-localized-image-and-how-do-i-create-one)


See Examples 1 and 2.

---

### Post by fvilaubi on 2013-01-10
Re #5: this bug is exactly I am  experiencing. I marked "I am affected" in two bugs.
Thanks Bufeu.

---

### Post by fvilaubi on 2013-01-10
Re #6: Is not a installation problem. I was using in locale catalan firefox 17.0 yesterday, until I receive the firefox 18.0 update. After "you must reinitialize Firefox" message, I only get English menu. 

This bug [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1098312) explains issue origins. (malformed install.rdf. There are 2 lines of whitespace at the start of the file, which results in the addon manager not loading it)

Thanks forkandles for your suggestion.

---

### Post by Margaret Dumont on 2013-01-11
Hello,

I've got exactly the same problem and I've already registered as well that I'm affected by both bugs, but does anyone now any workaround that might fix it so that we don't have to wait for the official update to do it for us?

By the way, how long does it normally take to fix Mozilla bugs like this?

Thanks!

         Margaret

---

### Post by fvilaubi on 2013-01-11
Hello Margaret

You can also look for in Catalan LoCo Team, this is the Post:
[http://ubuntuforums.org/showthread.php?p=12449201#post12449201](http://ubuntuforums.org/showthread.php?p=12449201#post12449201)

In Catalan, of course  ;-)

---

### Post by Margaret Dumont on 2013-01-11
Great! I'll look there, thanks for your help!  :)

---

### Post by fvilaubi on 2013-01-23
Today, with language pack 18.0.1 update, catalan language works fine.
Thanks to all 

Francesc.

---

