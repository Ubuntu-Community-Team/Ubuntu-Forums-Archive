---
title: "How to Turn My USB Key Into An Offline Repository For Synaptic ?"
date: 2005-08-24
forum: Installation &amp; Upgrades
---

### Post by bernardo on 2005-08-24
Hello to everyone. 
I'm sorry if the question has been posted before but i couldn't find it. Here it is:

As i dont have a broadband internet connection to my PC, but i can access the internet from another PC, I'd like to be able to store some files on my USB key, then plug it into my PC and have Synaptic recognize it as an extra repository.
I use Hoary 5.4.

I've googled for that and the only response i got was : [http://ubuntuforums.org/archive/index.php/t-7455.html](http://ubuntuforums.org/archive/index.php/t-7455.html)

Some steps are still not clear for me:

- Should the directories on the key mimic the structure of the repositories for Synaptic to recognize it as one ? (like /hoary/main or hoary/restricted etc...)

- Is it enough to add "file://my_custom_repo/blablabla/blablabla/" in sources.list or do i need to do something else ? it seems i need to create or overwrite  Packages or something, as  some guy suggests in the above link to type "dpkg-scanpackages . /dev/null >Packages" . Is that correct ?

- As i copy the files form the online repository to my key, are there files i should to copy in addition to the packages i need, like some index file ? I guess so but i 'm not sure...

-should i keep the .deb packages somewhere on my HD once the files have been installed (hopefully !) or can i delete them for good ? Is that ok if i want to uninstall the software later ? 

Except for those issues, my USB is correctly recognized (hotplug works). No other issue so far.
Thank you for reading.

---

