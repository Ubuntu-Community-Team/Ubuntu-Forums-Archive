---
title: "Setup hangs at &quot;testing network repository&quot;"
date: 2005-04-21
forum: Installation &amp; Upgrades
---

### Post by boleak on 2005-04-21
Like the title says.
from [this thread](http://ubuntuforums.org/showthread.php?page=1&pp=10) I see it's trying to contact something on the internet. problem is I'm in a corporate envronment and there's a proxy in the way. (and why that thread is in warty I don't know).

This really needs to be fixed.

---

### Post by alainhenry on 2005-04-21
I had the same problem the day I installed Hoary, but that was the week-end just after the release.  Servers might have been busy or saturated.  I tried again 2-3 hours later and all went fine.  I assume you tried several times already ?

Alain

---

### Post by boleak on 2005-04-21
[QUOTE=alainhenry]I assume you tried several times already ?[/QUOTE]

yah 6 attempts, think I have it this time. 
Eventually got it installed by doing an expert install & skipping the apt-configure section. Not sure yet what the consequences of skipping the apt-configure are. 
In the last attempt, I installed without networking but that was a mistake, pain in the behind to get going once the install has finished.

I'm behind a firewall, the machine cannot directly connect to anything on the internet. Seems a little odd to make a direct connection to the internet a mandatory requirement to install... a cancel button during the connection or proxy config page prior to connecting would help!

---

### Post by boleak on 2005-04-21
[QUOTE=boleak]Not sure yet what the consequences of skipping the apt-configure are.[/QUOTE]

well I discovered that sudo is not setup... there goes all the gui admin... back to files

---

### Post by Wiggum on 2005-05-04
When it hangs do a ctrl-alt f2 to get to a console.

ps -A |grep apt

kill the process called "/usr/lib/apt/methods/http"

ctrl-alt f1 to get back to your installation.

This isn't recommended of course, I have no idea if it harms anything else, but it works for me :) You'll still need a hole poked in your firewall eventually.

---

### Post by wanger123 on 2005-05-13
Hey Boleak, I also had this problem the first 2 times I tried an install (behind company firewall). I aborted the install both times thinking there was a problem. But the last 2 times I've done it, I just left it for the 20-30 mins it takes to complete the apt setup and all is good.
Hope this helps others (be patient!)

wanger

---

### Post by tek on 2005-09-24
everybody:

don't know why but the 20-30 minute statement is also valid for me, behind a router with firewall on, firewall off or DMZ and firewall. Either case makes me waiting for almost 30 minutes between the "network repository" and "security updates" screens. after that, i found one more interesting thing: what's the default root password?

---

### Post by devkelso on 2005-09-24
A very poorly documented feature of debian-installer is setting the proxy environment variable.  To do this try the following:

* boot from cdrom (or any other install type but thats a different topic)
* at the **Boot:** prompt type **linux http_proxy='<my proxy server ip or dns><proxy port>'**
* install as normal

---

