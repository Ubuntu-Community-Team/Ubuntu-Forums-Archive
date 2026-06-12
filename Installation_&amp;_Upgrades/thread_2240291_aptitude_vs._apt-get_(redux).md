---
title: "aptitude vs. apt-get (redux)"
date: 2014-08-19
forum: Installation &amp; Upgrades
---

### Post by maclenin on 2014-08-19
Is there a substantive difference between aptitude and apt-get? Ok, you strike 1 less key when typing apt-get and apt-get seems to be in wider circulation. Is one "better" than the other?

I understand aptitude is more "greedy" when it comes to addressing dependency issues while removing (or purging) or installing - in this instance, greed is good? No?

For example, both of these commands (seem) to accomplish the same thing:
```
sudo aptitude remove libreoffice-base
```
```
sudo apt-get purge libreoffice-base libreoffice-report-builder-bin libreoffice
```
Though aptitude also has a purge option - the end result of running both of the above commands doesn't (seem to) reveal much difference? In practice, users of either command were ultimately able to get their libreoffice application successfully removed (and reinstalled). Perhaps, different options are deployed depending on which "apt" is run - but the end result is the same?

One other example:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
```
sudo apt-get update
sudo apt-get upgrade
```
Is there a substantive difference?

Thanks for any guidance or opinion!

---

### Post by vasa1 on 2014-08-19
Apt-get is the default is Ubuntu. I haven't found any need to install aptitude ...

More experienced people seem to prefer aptitude.

Here is some reading material I found by searching for "apt-get versus aptitude":
[http://superuser.com/questions/93437/aptitude-vs-apt-get-which-is-the-recommended-aka-the-right-tool-to-use](http://superuser.com/questions/93437/aptitude-vs-apt-get-which-is-the-recommended-aka-the-right-tool-to-use)
[http://askubuntu.com/questions/347898/whats-difference-of-apt-get-and-aptitude](http://askubuntu.com/questions/347898/whats-difference-of-apt-get-and-aptitude)
[http://askubuntu.com/questions/1743/is-aptitude-still-considered-superior-to-apt-get](http://askubuntu.com/questions/1743/is-aptitude-still-considered-superior-to-apt-get)
[http://unix.stackexchange.com/questions/767/what-is-the-real-difference-between-apt-get-and-aptitude-how-about-wajig](http://unix.stackexchange.com/questions/767/what-is-the-real-difference-between-apt-get-and-aptitude-how-about-wajig)
[http://debian-handbook.info/browse/wheezy/sect.apt-get.html](http://debian-handbook.info/browse/wheezy/sect.apt-get.html)

And though this is a bit dated: [http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/](http://raphaelhertzog.com/2011/06/20/apt-get-aptitude-%E2%80%A6-pick-the-right-debian-package-manager-for-you/)

---

### Post by ian-weisser on 2014-08-19
> **maclenin said:**
> Is one "better" than the other?

Matter of opinion.
Both tools are designed for the same purpose, and both do it well.
I used to find aptitude's curses-based interface more useful in non-GUI environments.

> **maclenin said:**
>  Is there a substantive difference?

No.
There are many small differences, but there are no common situations where one is preferable to the other.
They are both good, stable, package manager (apt) frontends.

---

### Post by maclenin on 2014-08-20
**vasa1** and **ian-weisser** - thank you for your replies.

Given this **[COLOR="#008000"]variation[/COLOR]** (at a minimum)...
```
sudo **aptitude** remove libreoffice-base
sudo **apt-get** purge libreoffice-base libreoffice-report-builder-bin libreoffice
```
...I have tended to prefer **aptitude** - as (in addition to its brevity) it also seems more (interactively - see below) comprehensive in addressing dependencies perhaps overlooked within the original command - e.g. - if "libreoffice-base" is being removed, shouldn't "libreoffice" and "libreoffice-report-builder-bin" be removed, as well?
```
The following actions will resolve these dependencies:

     Remove the following packages:  
1)     libreoffice                   
2)     libreoffice-report-builder-bin

Accept this solution? [Y/n/q/?] 

```

Thanks, again, for your comments!

---

### Post by ian-weisser on 2014-08-20
apt, the actual package manager, is designed that  'apt-get remove libreoffice-base' and 'aptitude remove libreoffice-base' should do the same thing. Both should resolve the two dependencies automatically.
'remove' vs. 'purge' also should work the same way in both.

---

### Post by maclenin on 2014-08-23
**ian-weisser!** I would like to agree with you, but this [apt-get comment from a libreoffice bug report]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1354557/comments/13") (especially, in conjunction with the **[COLOR="#008000"]variation[/COLOR]** I describe above re: *sudo aptitude remove libreoffice-base*) leads me to (still) believe that aptitude is more "apt" in resolving dependencies automatically....

---

