---
title: "Installing Sun JRE"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by lukemack on 2007-04-07
Hi,

I would like to install the Sun JRE which I have downloaded from the Sun site as outlined here:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_JRE_v6.0)

However, I get the following error:

luke@DeepThought:~/Desktop$ fakeroot make-jpkg jre-6u1-linux-i586.bin
Creating temporary directory: /tmp/make-jpkg.OXVmYU4753
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

No matching plugin was found.
Removing temporary directory: done

can anyone help? My eventual aim is to have any java apps run using the JRE rather than gij which seems to be causing problems with Azureus.

many thanks,

<L>

---

### Post by Biker45 on 2007-04-07
Try synaptics and search for JRE.

---

### Post by lukemack on 2007-04-07
I assume you mean the synaptic package manager. That only contains version 5 (i have all repositories enabled). Thanks for trying but I am looking for help on this specific error and install method.

---

### Post by phossal on 2007-04-09
I much prefer installing Java using the .bin file directly from SUN. For such things, I avoid the package managers at all cost. They suck. But I don't waste my time making a package out of the .bin file just to install it. Execute the .bin file directly, and then integrate it into update-alternatives as the default Java. There is a tutorial on how to do that around here somewhere. ;)

---

### Post by lukemack on 2007-04-09
thats lovely for you. however, i have no idea what you're talking about.

---

### Post by phossal on 2007-04-09
SUN makes their JRE (and more useful, their JDK) available at their website in the form of a .bin file. It's useful to grab it direct. The mods of Ubuntu Forums and the Ubuntu'nuts generally disapprove of SUN's method, but if you can't figure out why it's better, you can always revert to a package install. 

The tutorial is in my signature.

---

### Post by lukemack on 2007-04-09
ok - thanks.
i currently have gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7) installed (i think this comes with ubuntu as standard).

can / should i uninstall that first?

---

### Post by phossal on 2007-04-09
No. I don't. Update-alternatives will manage all of your installed "options" for Java. It's sort of the whole point - you can install as many "Javas" as you want, and switch between them with:

```
sudo update-alternatives --config java
```

---

### Post by lukemack on 2007-04-10
ok, i tried following your guide but when i do:

sudo update-alternatives --install /usr/bin/java java /usr/lib/Java6u1/bin/java

I get:

update-alternatives: --install needs <link> <name> <path> <priority>

I guess your command is missing the priority - what should this be?

thanks,

<L>

---

### Post by phossal on 2007-04-10
The priority is optional. I typically set mine to 300 so that it will default to that option, rather than any downloads I pull from packages. You can make it whatever you want, because it's easily overridden.

---

### Post by lukemack on 2007-04-11
I would disagree that its optional, as I had to enter it to get the command to work. I set it to 99 in the end. Anyway, I appear to be up and running and the aim, to have a azureus running without killing the cpu, has been achieved so thanks very much for your help and for persisting with a relative noob!

---

