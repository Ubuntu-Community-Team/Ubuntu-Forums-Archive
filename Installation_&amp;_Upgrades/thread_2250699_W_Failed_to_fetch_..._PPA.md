---
title: "W: Failed to fetch ... PPA"
date: 2014-10-30
forum: Installation &amp; Upgrades
---

### Post by enmapa on 2014-10-30
Hi all (new-old member from France) i'm encountering a problem updating ubuntu from terminal and ubuntu package manager, both. When i try sudo apt-get update && sudo apt-get upgrade my sys give me this: 

```
W: Failed to fetch http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nikount/orta-desktop/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

Now i'd try some workout found on the internet (forum here, askubuntu and many others), they let me r[COLOR=#333333][FONT=UbuntuRegular]emove the existing trusted GPG key from the folder [/FONT][/COLOR]/etc/apt/trusted.gpg.d/,
or remove the content of list with [FONT=Ubuntu Mono]sudo rm -fR /var/lib/apt/lists/*, but nothing worked and plus i have now my source lists completely empty.

What can i do? 
thanks en avantage[/FONT]

---

### Post by oldos2er on 2014-10-30
If you visit [http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/](http://ppa.launchpad.net/langdalepl/gvfs-mtp/ubuntu/dists/) you can see there's no trusty repo, raring is the last Ubuntu version listed and is EOL itself.  You need to remove that PPA from your sources.

> i'd try some workout found on the internet (forum here, askubuntu and many others), they let me r[COLOR=#333333][FONT=UbuntuRegular]emove the existing trusted GPG key from the folder [/FONT][/COLOR]/etc/apt/trusted.gpg.d/,
or remove the content of list with [FONT=Ubuntu Mono]sudo rm -fR /var/lib/apt/lists/*, but nothing worked and plus i have now my source lists completely empty.[/FONT][FONT=Ubuntu Mono]

This is why it's not a good idea to run commands, especially any 'sudo rm' commands, without knowing what they're going to do. In your case it was completely unnecessary and useless, as you found out.

After you've removed the PPA, run ```
sudo apt-get update
``` to regenerate your sources lists.
[/FONT]

---

### Post by enmapa on 2014-10-30
You're brave, Gandalf, problem is confidence in everybody :p, said so... i thank you for your answer first, and that said too i'm coming to ask you how do i do that?
I think source list may be empty at this point, as i said. So i need to reset the whole thing now? 

Thanks for your help

P.s. it's a bloody fight me and ubuntu, i assure you :)

---

### Post by oldos2er on 2014-10-30
In Software Center go to Edit -> Software Sources. You can add or remove PPAs from here.

---

