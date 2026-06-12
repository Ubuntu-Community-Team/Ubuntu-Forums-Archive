---
title: "How to make Pangolin desktop look like the old days..."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2012-04-27
Some people love the new Unity look on Ubuntu


Others like myself are keener on the old-school look


Here is a failsafe [insofar as...]   way to make your desktop look like 1924;  or more like say the heady old days of Karmic


I know there are other Ubuntu users who like the old days;   like wearing a medieval costume on the 2012 streets of LA


So here goes...



First open terminal

```
sudo apt-get install gnome-shell

```
Then

```
sudo apt-get install gnome-session-fallback

```

Then [and without this it does not show anything on reload]
you need to go to startup applications [ go to Unity top left start button and enter startup  it will show up in the applications]


and add a new entry called gnome with the following command


```
gnome-panel --replace


```

[B]I think that is the quickest route and leaves no trace of the present
[/B] 

also if you are not going to use it


```
sudo apt-get remove unity

```

And live in the past like cars have not yet been invented  ... or computers... or ... tinned food.. 

 [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]  [img]http://img838.imageshack.us/img838/5745/smilie33.png[/img]

---

### Post by kansasnoob on 2012-04-27
No need to add 'gnome-shell' or remove 'unity'!

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by techsupport on 2012-04-27
> **kansasnoob said:**
> No need to add 'gnome-shell' or remove 'unity'!

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I really like the Ubuntu Fallback Session in 12.04 much more than previous versions of Ubuntu. At least try Fallback first, since it is just so much easier to install. You don't have to install any third party PPAs either to change to Fallback either.

---

### Post by shantiq on 2012-04-27
> **techsupport said:**
> I really like the Ubuntu Fallback Session in 12.04 much more than previous versions of Ubuntu. At least try Fallback first, since it is just so much easier to install. You don't have to install any third party PPAs either to change to Fallback either.


yes it is much easier than was previously, which is nice:KS

---

