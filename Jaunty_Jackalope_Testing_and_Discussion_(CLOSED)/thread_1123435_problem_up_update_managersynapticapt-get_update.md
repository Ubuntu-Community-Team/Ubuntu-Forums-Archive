---
title: "problem up update manager/synaptic/apt-get update"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lusephur on 2009-04-12
there is probably a very simple solution to this but, alas it eludes me, (long night last night ) 
trying to update and get the following message 
> A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/Release](http://archive.ubuntu.com/ubuntu/dists/jaunty/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
 

of course i get the same message when i run apt-get update, i've gone to the the address, moved up a level and copied the gpg and made a txt file and added it to the authorization section of software sources, and still same issue, 

as i said, most likely an easy solution, but one which right now escapes me.

any ideas?  
is the server down???

---

### Post by bubba_169 on 2009-04-12
Go to System -> Admin -> Software Sources and try selecting a different server in the "Download from:" box. Just an idea...

---

### Post by lusephur on 2009-04-12
tried that mate, alas same error, tried it from main server, tried it from Ireland server (where i am) tried it from Icelandic server and even ran the pick best server for me which gave me a Netherlands one, all with the same result, 

any more ideas though will be most welcome.

---

