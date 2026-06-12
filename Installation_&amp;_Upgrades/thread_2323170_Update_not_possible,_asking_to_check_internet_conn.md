---
title: "Update not possible, asking to check internet connection all the time."
date: 2016-05-03
forum: Installation &amp; Upgrades
---

### Post by shivam-19mishra on 2016-05-03
I recently upgraded to 16.04 LTS; After cstate = 1 all was fine until I installed some PPAs for conky and tomahawk, since then I am unable to update using apt-get update or update manager.

This is the message that I get:

W:The repository 'http://ppa.launchpad.net/costamagnagianfranco/ettercap-stable-backports/ubuntu xenial Release' does not have a Release file., 
W: Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:The repository 'http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu xenial Release' does not have a Release file., 
W: Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details.,
 W:The repository 'http://ppa.launchpad.net/tomahawk/ppa/ubuntu xenial Release' does not have a Release file., 
W: Data from such a repository can't be authenticated and is therefore potentially dangerous to use., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:Failed to fetch [http://ppa.launchpad.net/costamagnagianfranco/ettercap-stable-backports/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/costamagnagianfranco/ettercap-stable-backports/ubuntu/dists/xenial/main/binary-amd64/Packages) ;404 Not Found, 
E:Failed to fetch [http://ppa.launchpad.net/costamagnagianfranco/ettercap-stable-backports/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/costamagnagianfranco/ettercap-stable-backports/ubuntu/dists/xenial/main/binary-i386/Packages) ;404 Not Found, 
E:Failed to fetch [http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/xenial/main/binary-amd64/Packages) 404 Not Found, 
E:Failed to fetch [http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/ralf.hersel/rhersel-ppa/ubuntu/dists/xenial/main/binary-i386/Packages) 404 Not Found, 
E:Failed to fetch [http://ppa.launchpad.net/tomahawk/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/tomahawk/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages) 404 Not Found, 
E:Failed to fetch [http://ppa.launchpad.net/tomahawk/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/tomahawk/ppa/ubuntu/dists/xenial/main/binary-i386/Packages) 404 Not Found, 
E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks in advance for your help.

---

### Post by grahammechanical on 2016-05-03
Now that you have installed that software disable those PPAs. As you can see it is the PPAs that are coming up with the "404 Not Found" error messages. Disable those PPAs in System Settings>Software & Updates>Other Software.

If you have not been able to install the software it is most likely that those PPAs have not been made available for Ubuntu 16.04. Each version of Ubuntu has its own software repositories and the code name for that version is part of the URLs to its repositories. When we run a command to install a PPA the URL is automatically given the code name of the version of Ubuntu that we are using as part of its URL.

So, the URLs for those PPAs include the code name xenial. But if the developer has not yet created a PPA for xenial we will get a "404 Not Found" message.

Regards.

---

### Post by shivam-19mishra on 2016-05-03
Thanks a lot Grahammechanical. It solved the issue. I wish I knew Ubuntu as much as you all do so I wouldn't bother people with stupid queries :)

And thanks also for the info on PPAs working, that will sure help in the future.

---

