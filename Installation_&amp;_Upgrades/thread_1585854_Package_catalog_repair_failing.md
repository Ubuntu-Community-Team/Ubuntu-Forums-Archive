---
title: "Package catalog repair failing"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by ArkticMud on 2010-10-01
I am running a 64bit 10.10 with gnome. Its pretty much a fresh install. I saw a project called CAINE, it looked neat so I'd thought I'd give it a try, something in the installation mucked up. Now when I open the Software center I get a message telling me "Items can no be installed or removed until the package catalog is repaired" I click repair and I get this error message: E:I wasn't able to locate file for the caine-from-deb package. This might mean you need to manually fix this package.: 

So I thought I'd give it a go using synaptic package manager, it gives me these error messages: E: caine: subprocess installed post-removal script returned error exit status 2
E: caine-from-deb: subprocess installed post-removal script returned error exit status 2

I am currently unable to install or update any software at the moment so I really need help to get this fixed.


Thanks, ask if you need any more info!

This is the CAINE package thing I attempted to install: [http://www.soluzioni.org/caine/howto/](http://www.soluzioni.org/caine/howto/)

---

### Post by Coughanour on 2010-10-19
Ran into the same problem, same package. To fix it go into /var/lib/dpkg/info and do a search for the word caine and delete those files. After that dpkg will be able to remove it without an issue. I think the overall problem is that one of the shell scripts in there is nothing but comments. Anyway, hope it helped.

---

### Post by rmcellig on 2011-04-22
I have the same issue where I am always asked to repair the Package catalog. How do I do this? I tried looking for Caine in the info file but there were no instances of that text. What next?

---

### Post by Ranga Swamy Chakali on 2012-03-06
i am also struggling with same error can you please give suggestion on that 

  sudo apt-get install -f , also not working .


Thanks 
Ranga Swamy
[email]crswamy929@gmail.com[/email]
9620720182

---

