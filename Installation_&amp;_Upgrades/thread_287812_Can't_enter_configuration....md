---
title: "Can't enter configuration..."
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by ianpeters on 2006-10-29
Just upgraded to Edgy which was quite painless. But now I can't enter certain administration utilities. Before it showed the "enter password" dialog, now it just shows that I don't have the rights. Does anyone know how to solve this? Strange thing is, the Synaptic and Update-manager tools still display the dialog.

Thank you in advance!


EDIT: I just noticed that I can't enter the "User and groups" and "Services" options as well. Quite irritating :evil:

---

### Post by ianpeters on 2006-11-03
Well....still nobody who's seens this problem?

---

### Post by taurus on 2006-11-03
What's the output of this command from a prompt, terminal, then?

```
id
```

---

### Post by ianpeters on 2006-11-07
batman@pavilion:~$ id
uid=1000(batman) gid=1000(batman) grupper=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(lpadmin),108(scanner),1000(batman)
batman@pavilion:~$ 


That's the result.

---

### Post by taurus on 2006-11-07
You also need to belong to group admin in /etc/group.  So, boot into recovery mode from GRUB and add yourself, batman, to group admin in /etc/group...

```
nano -Bw /etc/group
```

---

### Post by ianpeters on 2006-11-09
OK, so I think I figured out the problem. During the upgrade it seems 'gksu' got lost from the linking in the menus and therefor I got the error message not being able to give a password.

All is well now, thank you for your help guys.

---

