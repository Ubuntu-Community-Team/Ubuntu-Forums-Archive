---
title: "When this bug will be solved???"
date: 2010-02-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by eshant_engineer on 2010-02-01
_**Device:**_ ZTE EvDO ac8700 Rev0(with operator BSNL,India and Reliance,India)

_**Problem:**_ Network Manager not able to connect.

_**From when? :**_ Before Jaunty we were using wvdial package to establish connection then Jaunty was launched and we got gift as the network manager was now recognising the device as **"Auto Mobile CDMA Connection"** and establishing the the connection. But in Karmic [[COLOR="Red"]_**[SIZE="4"]this bug[/SIZE]**_[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213") ruined down the situation and **Lucid is also carrying on with this bug**. I had tried it on VM to check whether or not the bug is fixed but again the same disappointment.

_**Effect:**_ We are not able to use Empathy and many other apps which check connection from network manager and **most inconvenient thing is to dial and disconnect manually with bit long waiting time**.

I don't know where is the right place to inform this thing. But if you know then please let me know so that I can put it over there.

Thank You...

---

### Post by dino99 on 2010-02-01
have you a bug number on launchpad ? Try to report this bug if not already done.

def: any problem without bug report is not a bug.  ;)

---

### Post by xens on 2010-02-01
another way is to test the git version of network-manager to see if this bug is already close upstream. If not you can report this bug to the network-manager mailing list.

---

### Post by autark on 2010-02-01
> **dino99 said:**
> have you a bug number on launchpad ? Try to report this bug if not already done.

If you look closely, there is a link to the Launchpad bug (321213) in his message.

---

### Post by alexmurray on 2010-02-01
The bug is marked as solved from a year ago - are you sure this is the correct bug? If not, file a new one.

---

### Post by eshant_engineer on 2010-02-02
> **xens said:**
> another way is to test the git version of network-manager to see if this bug is already close upstream. If not you can report this bug to the network-manager mailing list.
git version of network manager!!!! please give few more details.

> **alexmurray said:**
> The bug is marked as solved from a year ago - are you sure this is the correct bug? If not, file a new one.
I found three bug reports on launchpad
[[COLOR="Red"]first[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/234283")
[[COLOR="Red"]second[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/hal-info/+bug/321213") 
[[COLOR="Red"]third[/COLOR]]("https://bugs.launchpad.net/network-manager/+bug/461096")

Please let me know where can I find Network Manager logs and what else is necessary to report?

Thank You...

---

### Post by autark on 2010-02-02
> **eshant_engineer said:**
>  Please let me know where can I find Network Manager logs and what else is necessary to report?

See [https://wiki.ubuntu.com/DebuggingModemmanager](https://wiki.ubuntu.com/DebuggingModemmanager) for some debugging hints.

---

### Post by dino99 on 2010-02-02
run into console;

ubuntu-bug << your package >>

it will find and send all the needed things for you. :p

---

### Post by kunalgautam on 2010-02-20
Even I reported about it long time ago, but no reply :( [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/490247](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/490247)

---

### Post by Taiebot65 on 2010-02-20
Have you tried to install the package usb-modeswitch it might be just that ..

---

