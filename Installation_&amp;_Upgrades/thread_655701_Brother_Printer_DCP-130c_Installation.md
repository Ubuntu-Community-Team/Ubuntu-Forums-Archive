---
title: "Brother Printer DCP-130c Installation"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by Paul Vega on 2008-01-01
Hello All

I have recently become MS free and love the idea although I am struggling with understanding where files etc are stored in Ubuntu. I have followed some of the threads re the issue of Brother DCP-130c installations and have become bogged down with talk of editing the driver (but I am relishing the challenge). On top of that, and the main reason why I am posting, is that I have now got the following message when I go to update: 
Could not initialize the package information

**A unresolvable problem occurred while initializing the package information.**

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package dcp130ccupswrapper needs to be reinstalled, but I can't find an archive for it.'

Can anyone help me to resolve this issue please?

Paul Vega

---

### Post by Partyboi2 on 2008-01-01
You could try this:
> ```
gksudo gedit /var/lib/dpkg/status
```Find the log for Brother lpr and it should say that it halfway installed. Delete the entry and save.
You can now go to Synaptic or whatever you like and delete the partially installed package.
here is the link
[http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000](http://ubuntuforums.org/showthread.php?t=515125&highlight=brother+dcp+1000)

---

### Post by Paul Vega on 2008-01-02
Thanks Very Much...
I followed the instructions and have now gotten rid of the offending error message. I completed the installation as recommended and it all looks good...except that nothing prints. The printers display says that data is being received but there is no action whatsoever other than that! Can you or anyone else help?

Paul V

---

