---
title: "Can't get new update need help!!! I keep getting the same error 404 not found"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by san_antonio9.10 on 2010-02-24
[IMG]http://ubuntuforums.org/images/rank_1.png[/IMG]
 			  			  			 				 
				Join Date: Feb 2010
 				 				 	  					Beans: 1 				
 			   				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Update ubuntu 9.10** 			
 			 			 		   		 		 		Good Evening Guys !!!! I got a small problem. I can't get the last update for ubuntu 9.10 I try via command & archive manager and keep getting the same error; any help would be appreciated thanks ... Failed to fetch [http://ppa.launchpad.net/ubuntu-wine...86/Packages.gz]("http://ppa.launchpad.net/ubuntu-wine/p/ubuntu/dists/karmic/main/binary-i386/Packages.gz")  404  Not FoundE: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by adam814 on 2010-02-24
Either edit the source line for that PPA in software sources or /etc/apt/sources.list manually.

The link you post is this:
```
http://ppa.launchpad.net/ubuntu-wine/p/ubuntu/dists/karmic/main/binary-i386/Packages.gz
```

It should be this:
```
http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz
```

That should do the trick, when I enter that in my browser I get prompted to open or save the file.

---

### Post by san_antonio9.10 on 2010-02-25
[SIZE=5]**Thank you Adam814 your information was really helpfu**l[/SIZE]

---

