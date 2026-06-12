---
title: "Linux Mint 16 + Samba 3 DFS"
date: 2014-01-08
forum: MINT
---

### Post by tporter on 2014-01-08
Greetings,

I have been working on replacing a Windows server that has a simple DFS on it.

Since the server is now in its death throws.... I was setting up a new machine to take over but ran in to a oddity.

I was unable to get the Samba 3 DFS to work using Linux Mint 16 Desktop.

I moved to vm to test.

I created a new Linux Mint 16 Desktop in VirtualBox, default install settings.

Version: Linux Mint 16 Petra

Updated to the latest apt-get update, apt-get upgrade, then rebooted.

I configured Samba 3.6.18 as follows to create a DFS, with the following instructions.

```

mkdir /usr/local/samba/dfs
chown root:root /usr/local/samba/dfs
chmod 755 /usr/local/samba/dfs
cd /usr/local/samba/dfs
ln -s 'msdfs:maya\e' maya-e

vim /etc/samba/smb.conf

```

Added to the [global]

```

host msdfs = yes

```

Added at the end of the file.
```


[dfs]
path = /usr/local/samba/dfs
msdfs root = yes


```

Restarted service..

```

service smbd restart

```

On my Windows machine \\machine, but it prompts for a password.

Same as my other Mint machine.

I had orginally did this in a Minimal Ubuntu 13.10 Server and it had worked, so I repeated the process to confirm.

Created a Ubuntu 13.10 Minimal (saucy), selected OpenSSH and Samba during the install.

Did the above to create a DFS, and when went to the windows machine and \\machine2 tada it has the maya-e and I can open browse, create, etc...

Is there something I'm missing?

Thanks for reading,
Terre

---

