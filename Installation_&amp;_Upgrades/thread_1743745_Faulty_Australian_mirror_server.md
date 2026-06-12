---
title: "Faulty Australian mirror server"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by STEVE777 on 2011-04-29
I am trying to upgrade from 10.10 to 11.04 but get error:

Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu1_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-common_3.3.0-7ubuntu1_all.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org_3.3.0-7ubuntu1_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org_3.3.0-7ubuntu1_all.deb) 404  Not Found [IP: 211.29.132.60 80]
Failed to fetch [http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu1_all.deb](http://mirror.optus.net/ubuntu/pool/universe/o/openoffice.org/openoffice.org-gtk_3.3.0-7ubuntu1_all.deb) 404  Not Found [IP: 211.29.132.60 80]
etc. There are many more.

How can I force it to upgrade from a different server? What other servers are available?

Thanks for any help.
Steve.

---

### Post by Rhubarb on 2011-04-29
The internode server in Australia seems to be fine:
mirror.internode.on.net

- Well, at the very least it worked fine last night for me.
  I haven't tried it this morning yet.

---

### Post by STEVE777 on 2011-04-29
Thanks Rhubarb
But how do I force it to use that server? The upgrade tool doesn't allow me to choose a server. Is there a way to upgrade using terminal?

---

### Post by Githlar on 2011-04-29
STEVE, first, make a backup of your old sources list:
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```

Then, open up your /etc/apt/sources.list file using the command:

```
sudo gedit /etc/apt/sources.list
```

Now, do a find and replace and replace all instances of:
"au.ubuntu.com" (or whatever you current mirror is) with "mirror.internode.on.net/pub/ubuntu" and save the file.

The final lines should look something like:
```
deb http://mirror.internode.on.net/pub/ubuntu/ubuntu maverick main
```

Follow that command with a:
```
sudo apt-get update
```

Now, try running the updater again.

---

