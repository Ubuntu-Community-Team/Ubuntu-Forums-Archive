---
title: "Can't Access Windows Networks on Jaunty"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by beastrace91 on 2009-03-31
Hey,

So I formatted to the Jaunty beta today, and I went to access my network shares to copy my files back over an I can no longer load them up... I see the "windows network" and then my network within that (its called "hobnw") but when I double click to view the computers in the network I get an "Unable to mount location - failed to retrieve file from server" Any ideas what I need to do get this working? It was working under Ibex just fine.

Thanks,
~Jeff

---

### Post by cariboo on 2009-04-01
You may have to change you workgroup to the same as the other computers. Press Alt-F2 and type:

```
gksu gconf-editor
```

then click system-->smb, you will see workgroup in the right pane. RIght-click workgroup and select Edit key, type your workgroup name and click OK. You may need to reboot in order for the new workgroup name to change.

Jim

---

### Post by geraner on 2009-04-09
This solution doesn't work. :(

I still get the message:> 
Unable to mount location
Failed to retrieve share list from server

Any further solutions?

Samba worked perfectly in 8.10 for me.
Now in Jaunty it stoped working. :(

---

### Post by excogitation on 2009-04-09
Fyi it does still work over here.

Did you try using Places -> Connect to server -> Windows Share
and provide your credentials?

---

