---
title: "Is there a list of packages not installed on a reinstall of the os"
date: 2015-07-10
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2015-07-10
[I]"An error occurred whilst restoring previously installed packages. The installation will continue but you may have to manually reinstall some applications after the computer reboots."
[/I]
This message came at the end of a reinstall of Ubuntu 14.04. It would be helpful if I knew which applications had not been reinstalled. Is there a log somewhere?

---

### Post by Bashing-om on 2015-07-10
Robbyx; Ouch;

A very open ended question, that can have any number of different answers.
> 
This message came at the end of a reinstall of Ubuntu 14.04.

Begs the question that of internet connectivity ? A wired connection in use ?

3rd party software ? In the (RE-)install process, did you dis-able all 3rd party  sources ?

To see the current status of installed/not installed packages, run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```

With these results we get an indication of where to go from here.

> 
Is there a log somewhere?

Maybe, take a look at:
```

cat /var/log/dpkg.log

``` for anything interesting.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Robbyx on 2015-07-10
Thanks. I went ahead and manually installed all the programs having config files  in my home directory. It seems to have worked but it is not very helpful of Ubuntu to report that there has been a failure to reinstall all the programs and not indicate which ones failed!

---

### Post by kansasnoob on 2015-07-10
When you perform an upgrade or reinstallation using the live media the logs are created in /ubiquity-apt-clone rather than /var/log:

[http://ubuntuforums.org/showthread.php?t=2242056&p=13111389#post13111389](http://ubuntuforums.org/showthread.php?t=2242056&p=13111389#post13111389)

That said I've never really spent the time to parse the logs myself.

---

