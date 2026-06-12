---
title: "Evolution mail notification problem"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by randlieb on 2008-11-06
I upgraded to Ibex and everything went smoothly. Desktop and all apps function fine....except the following ...

I have used the 'mail-notification-evolution' package from synaptic with my Hardy system and it worked fine. I like it because it has more options and functionality than the default mail-notification daemon. Now with the Ibex upgrade when I have the mail notification-evolution open and then open Evolution, Evolution crashes. Same when I have Evolution open and then open  mail-notification-evolution, Evolution crashes. They don't seem to be able to work together anymore.

Any help greatly appreciated.

---

### Post by Coreigh on 2008-11-06
Please forgive my ignorance but what does that package provide?

I am not on 8.10, I am still on 7.10 with Evolution 2.12.1 but when I get an email I get a flashing mail icon in the panel near the clock and I get a audible chime. I checked and I do not have mail-notification-evolution installed.

---

### Post by randlieb on 2008-11-06
If you have multiple folders in Evolution you can determine which folders notify you when new mail arrives. You also have the ability to allow pop-ups for each new email to remain visible until you click on them. You can set how long they remain visible, number of minutes or forever (or until you read the mail).

After you've installed through Synaptic you go into Evolution and click on 'edit > plugins' and check the 'Jean-Yves Lefort's Mail Notification' and uncheck the 'Mail Notification'.

A much more handy tool than the default...WHEN IT WORKS!!!!

---

### Post by ]grimm[ on 2008-11-08
> **randlieb said:**
> I upgraded to Ibex and everything went smoothly. Desktop and all apps function fine....except the following ...

I have used the 'mail-notification-evolution' package from synaptic with my Hardy system and it worked fine. I like it because it has more options and functionality than the default mail-notification daemon. Now with the Ibex upgrade when I have the mail notification-evolution open and then open Evolution, Evolution crashes. Same when I have Evolution open and then open  mail-notification-evolution, Evolution crashes. They don't seem to be able to work together anymore.

Any help greatly appreciated.

I am having the exact same problem with mail-notification and evolution.  Evolution crashes whenever mail-notification is configured to monitor evolution folders for new mail in Intrepid Ibex.  However, unlike the original poster, I can't seem to get the default mail-notification option to appear in my plugin list.

---

### Post by Nickrw on 2008-11-10
I experienced the same problem with a new install of Intrepid. I'm using evolution with an exchange mailbox.

The notification setup seems to have problems with locating specific mail folders - if I select 'Personal folders' within my exchange account when adding a folder to monitor, then under the 'Details' tab click 'Other' and enter the name of the specific folder it adds it to the list without giving an error / crashing.

---

### Post by dandu on 2008-11-16
it's a bug: [https://bugs.launchpad.net/mail-notification/+bug/251031](https://bugs.launchpad.net/mail-notification/+bug/251031)

fixed installing the packages from here: [http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/](http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/)

---

### Post by randlieb on 2008-11-16
> **dandu said:**
> it's a bug: [https://bugs.launchpad.net/mail-notification/+bug/251031](https://bugs.launchpad.net/mail-notification/+bug/251031)

fixed installing the packages from here: [http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/](http://ppa.launchpad.net/jsteinhart/ubuntu/pool/main/m/mail-notification/)

Hooray!! That fixed it though it took a couple starts and restarts of both apps to get the pop-ups to show. Don't know why that was. And yes I had to install both debs. When I tried just the 'evolution' pkg it showed dependencies unsatisfied. Installed the 'mail-notification' pkg first and the 'evolution' one installed fine.

Read the bug thread you sent. Very informative as to the inner workings of what was done. Will follow the advice and not change the sources.list.

---

