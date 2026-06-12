---
title: "apt-get update problem"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by absent_minded2 on 2013-08-21
**If I run "apt-get update" command in terminal, the update process works well at starting time but end of the process the following errors happened.**


> Ign [http://download.opensuse.org](http://download.opensuse.org) ./ Translation-en_US          Ign [http://download.opensuse.org](http://download.opensuse.org) ./ Translation-en             
Err [http://download.opwnsuse.org](http://download.opwnsuse.org) ./ Sources
  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)
Err [http://download.opwnsuse.org](http://download.opwnsuse.org) ./ Packages
  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)
Err [http://download.opwnsuse.org](http://download.opwnsuse.org) ./ Translation-en_US
  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)
Err [http://download.opwnsuse.org](http://download.opwnsuse.org) ./ Translation-en
  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)
W: Failed to fetch [http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Release.gpg](http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Release.gpg)  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Sources](http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Sources)  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Packages](http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./Packages)  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./en_US](http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./en_US)  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./en](http://download.opwnsuse.org/repositories/home:/sarimkhan/xUbuntu_12.04/./en)  Something wicked happened resolving 'download.opwnsuse.org:http' (-5 - No address associated with hostname)


E: Some index files failed to download. They have been ignored, or old ones used instead.


How can I solve this problem. The domain name is wrong here, It's ***opensuse.org*** but here it's shown ***opwnsuse.org***. Is there anyway to make correction on this domain name? and in which directory all these **urls** are been saved??

---

### Post by ukbeast on 2013-08-21
Are you sure you are using Ubuntu? that looks like you are using opensuse :P

---

### Post by absent_minded2 on 2013-08-21
I've just installed ibus-avro from opensuse.org

---

### Post by ukbeast on 2013-08-21
Try this to restore back to Ubuntu's default sources [http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)

---

### Post by absent_minded2 on 2013-08-21
> **ukbeast said:**
> Try this to restore back to Ubuntu's default sources [http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html](http://www.tuxgarage.com/2011/01/restore-your-sources-list-to-defaults.html)

Its not working... My problem is not yet solved :(

---

### Post by cortman on 2013-08-21
You need to answer the first question asked: Are you using Ubuntu or OpenSUSE?

---

### Post by grahammechanical on 2013-08-21
I may not know much about anything but I keep seeing "No address associated with hostname" as you do. It seems to me that installing that package from Opensuse has put a link in your software sources list to an Opensuse repository that is broken by a typing error at the Opensuse end of things. Uninstall that package and may be the sources list will be cleaned up.

Are you still able to update the sources list and run apt-get upgrade? Do you get failures at that stage of things?

/etc/apt/

Regards.

---

### Post by absent_minded2 on 2013-08-21
> **grahammechanical said:**
> I may not know much about anything but I keep seeing "No address associated with hostname" as you do. It seems to me that installing that package from Opensuse has put a link in your software sources list to an Opensuse repository that is broken by a typing error at the Opensuse end of things. Uninstall that package and may be the sources list will be cleaned up.

Are you still able to update the sources list and run apt-get upgrade? Do you get failures at that stage of things?

/etc/apt/

Regards.
[B]
Thanks. Its solved. I've uninstalled that software and then install it again.. :-)[/B]

---

