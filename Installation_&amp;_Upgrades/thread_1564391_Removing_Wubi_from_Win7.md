---
title: "Removing Wubi from Win7"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by p0ntiac on 2010-08-30
Hi all,
I need a little help fully removing wubi from my Windows, because I formatted the linux partition where the ubuntu install was, and I can't install it again. If I start wubi, it tells me please first uninstall. I go to the uninstaller, it pops up with an error: 
"Error executing command: command=C:\...\bcdedit.exe /delete"
..here comes a registry key...
"stderr = An error occured while attempting to delete the specified entry. The system cannot find the file specified."
And gives a huge log file.

I guess it searches for files, or keys, can I delete all chunks to run again the wubi installer?
Any idea?

Thanks

---

### Post by cazador31 on 2010-08-30
Go to drive C and programs files. Delete the Ubuntu folder and you will be good to go

---

### Post by p0ntiac on 2010-08-30
Hi,
I don't have such directory.. :( 
I only have the ubuntu dir on the partition made for linux.

---

### Post by cazador31 on 2010-08-30
Go to windows drive C program files. The Ubuntu folder is in there. Delete it. I had the same exact problem when I tried to uninstall Wubi. The folder will be empty, but for some reason you have to delete it.

---

### Post by p0ntiac on 2010-08-30
Can you trust me I don't have the Ubuntu dir there? I checked also if it's hidden. May I take some screenshots about the dirs? Maybe the installer has started to remove it, or stg..

---

### Post by p0ntiac on 2010-08-30
The error appears: [http://s797.photobucket.com/albums/yy257/doiturself/?action=view&current=wubi_error.jpg](http://s797.photobucket.com/albums/yy257/doiturself/?action=view&current=wubi_error.jpg)

...

and I found the key in registry, it's the value of "VistaBootDrive".. if it helps

---

### Post by p0ntiac on 2010-08-30
PROBLEM SOLVED!

I found only one entry in the registry with wubi, and deleted all keys. After a restart(!), the wubi installer stared and now I'm under linux again.

cazador31 - Thanks for the suggestions!

---

### Post by cazador31 on 2010-08-30
The Ubuntu folder was in the Drice C folder. My mistake. It's not in the programs folder. Sorry about that.  I had the same message as your screen shot said and I fixed it by uninstalling the folder.  Seems to me it should be ithe drice c folder

---

