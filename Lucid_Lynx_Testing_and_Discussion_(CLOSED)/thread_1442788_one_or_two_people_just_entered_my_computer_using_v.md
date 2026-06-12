---
title: "one or two people just entered my computer using vino"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-30
i was watching my computer and suddenly got some users are watching my computer i disconnected then i noticed that my cpu is working at 100% i checked and saw a process called vino i disable it then then disabled remote desktop and all sort of sharing i have here uninstalled vino  what is this vino server is it a default software (remote desktop?) and what can i do to prevent this problem again?

thanks in advance.

---

### Post by lisati on 2010-03-30
One approach might be to quickly save what you're doing and restart: near instant disconnection before they can do any damage.

---

### Post by _h_ on 2010-03-30
> **lisati said:**
> One approach might be to quickly save what you're doing and restart: near instant disconnection before they can do any damage.

And what is stopping them from near instantly reconnecting when the service starts again?

There's an option under System -> Preferences -> Remote Desktop that allows you to allow or deny access.

---

### Post by sdowney717 on 2010-03-30
I just tried to enable it and its only available to my local netowrk.
Since I am my own local network, no risks at all. How would you configure this to let users outside your LAN access your desktop?

---

### Post by _h_ on 2010-03-30
> **sdowney717 said:**
> I just tried to enable it and its only available to my local netowrk.
Since I am my own local network, no risks at all. How would you configure this to let users outside your LAN access your desktop?

You must be behind a router?

---

### Post by lisati on 2010-03-30
> **_h_ said:**
> And what is stopping them from near instantly reconnecting when the service starts again?

There's an option under System -> Preferences -> Remote Desktop that allows you to allow or deny access.

It gives the OP a chance to investigate and look into the means to tighten up....

---

### Post by sdowney717 on 2010-03-30
yes, actually 2 routers. Double NAT

[http://ask-leo.com/what_is_double_natting.html](http://ask-leo.com/what_is_double_natting.html)

---

### Post by aviramof on 2010-03-30
i too have the same message in remote desktop and yet they got it also i now marked display icon only when someone is connected and yet the icon is still there despite the fact i just downloaded and installed gufw and turn it on and no one is connected i think maybe it has something to do with all the updates i downloaded today maybe a security bug in one of them.

EDIT:
i have just disconnected and yet the icon stays on the top panel  despite the fact that in preference it set show icon when someone is connected.

---

### Post by doas777 on 2010-03-30
vino is the process under which ubuntu's remote desktop server runs
it is a variation of the VNC protocol. if you disable the ubuntu remote desktop, in system -> Preferences then the intrusions shoudl stop. 

it is not safe to use vino when you are not behind a firewall, so be sure to keep it disabled until you can get a router.

---

### Post by cariboo on 2010-03-30
Just to add to what doas777 said, vino is one of the most often causes of a system getting cracked, it is usually due to a weak or no password. I would suggest using ssh with private keys to access a remote system.

---

### Post by aviramof on 2010-03-30
and yet i had no problems with it till now and not the problem i mentioned earlier about the icon in the top panel always there even when there is no one connected was there any update today to vino or something else related to that?

---

### Post by doas777 on 2010-03-30
> **aviramof said:**
> and yet i had no problems with it till now and not the problem i mentioned earlier about the icon in the top panel always there even when there is no one connected was there any update today to vino or something else related to that?
not sure about the icon. I've never had a problem with that. 

no, most likely a port sweep didn't notice that you had that port open until today. I haven't had a vino update in some time, but even if you did, the service is doing exactly what it is supposed to.

vino/vnc is not at all secure by itself. letting them right in is what it is supposed to do. vino does little or nothing to stop ***anyone*** from connecting. you need to rely on other controls like firewalls and whatnot to make it safe.

as Cariboo pointed out, SSH is a much more secure means for remote access. I use FreeNX (which uses ssh's security) to connect to remote workstations, and working with the desktop there graphically. the only vissible differance between it's output and Vino's is that in vino, the users share a desktop, in that when one moves the mouse, the other sees it. freenx runs in an independent session, so there is no interaction with the local user.

---

### Post by aviramof on 2010-03-30
there was a vino update today vino_2.2.8.1-2ubuntu1_i386.deb maybe he had something to do with this problem.

---

### Post by emarkay on 2010-03-30
Or, just Synaptic the pesky thing away forever.  :)

---

### Post by aviramof on 2010-03-31
there was another one just now let's hope it would fix every problem vino had.

---

### Post by Crunchy the Headcrab on 2010-03-31
Is Vino even on by default?  I just checked remote desktop and it says "Nobody can access your desktop."  I'm just curious if this is the default or if it's an affect of me going into startup applications and de-selecting remote desktop (which I did much earlier).

---

### Post by aviramof on 2010-03-31
Well it does exist in startup with the command /usr/lib/vino/vino-server --sm-disable

and i don't see that changing if i disable or enable it but it's still there by default.

---

