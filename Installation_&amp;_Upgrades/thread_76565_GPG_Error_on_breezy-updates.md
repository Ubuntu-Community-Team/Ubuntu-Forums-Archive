---
title: "GPG Error on breezy-updates"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by reuben on 2005-10-15
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by Gcool on 2005-10-15
I was able to solve this, in the following way:

System > Administration > Synaptic Package Manager
Settings > Repositories > Authentication > Restore default keys

And then do an "apt-get update" again.

---

### Post by rattaro on 2005-10-15
[QUOTE=Gcool]I was able to solve this, in the following way:

System > Administration > Synaptic Package Manager
Settings > Repositories > Authentication > Restore default keys

And then do an "apt-get update" again.[/QUOTE]


I have the same problem, but it does NOT get solved by restoring the default keys.  I'm not sure what or why this happened.  Any thoughts anyone?

---

### Post by azteech on 2005-10-16
[quote=Gcool]I was able to solve this, in the following way:

System > Administration > Synaptic Package Manager
Settings > Repositories > Authentication > Restore default keys

And then do an "apt-get update" again.[/quote]

This solution solved my problem. However, there is another recommended solution, which may also work -- see this thread - 

 
[http://www.ubuntuforums.org/showthre...d=1#post416599]("showthread.php?p=416599&posted=1#post416599")
  		  	  		  		  		  		  		  	  	  	                   		[RIGHT]  			  		    			  		  			[[IMG]http://ubuntuforums.org/images/element/buttons_blue/quote.gif[/IMG]]("newreply.php?do=newreply&p=416607")[/RIGHT]

---

