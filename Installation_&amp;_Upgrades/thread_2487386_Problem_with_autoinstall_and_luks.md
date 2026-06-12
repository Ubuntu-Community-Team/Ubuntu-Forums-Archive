---
title: "Problem with autoinstall and luks"
date: 2023-06-02
forum: Installation &amp; Upgrades
---

### Post by Jaxilian on 2023-06-02
Hi,

I am trying to get the new autoinstall with subiquity to work on 23.04 (training on it only). On the older deb-installer ubiquity, I could manage to get LUKS encryption to work when installing with preseed-files (i use that today). This new installer is tricky.

I tried this in my user-data file (according to [https://bugs.launchpad.net/subiquity/+bug/1913986](https://bugs.launchpad.net/subiquity/+bug/1913986))

```
  storage:
    layout:
      name: lvm_use_all_space
      password: TEMPORARY
```

but it just won't work. It goes through the whole installation automatically and uses lvm, but no encryption is made at all.

Hope someone could help me tell what I do wrong.

---

### Post by MAFoElffen on 2023-06-02
Here is what was said in the commit for that at GitHub:
> 
So I ran this branch through an autoinstall, with the following as input:
```

version: 1
identity:
    hostname: ai-test
    password: "$y$j9T$UdY22v4Kexn/AZcIzBSUc0$2DnuvWDSwoDCFPlbk1ghZeT2qFrEBKY1bpFQoexHdw7"
    username: ubuntu
storage:
    layout:
        name: lvm
        password: passw0rd

```
Then grepped the output. It would be best if we didn't log the contents of storage.layout.password, looks like there are 3 places that do so.
```

58:2023-03-02 03:11:53,211 DEBUG subiquity.server.controllers.filesystem:161 load_autoinstall_data {'layout': {'name': 'lvm', 'password': 'passw0rd'}}
59:2023-03-02 03:11:53,211 DEBUG subiquity.server.controllers.filesystem:162 self.ai_data = {'layout': {'name': 'lvm', 'password': 'passw0rd'}}
236:2023-03-02 03:11:53,639 DEBUG subiquity.server.controllers.filesystem:925 self.ai_data = {'layout': {'name': 'lvm', 'password': 'passw0rd'}}

```
Just remove those log statements for now and I'm good to land this.

Of course, if you look at the new (readme) for the subiquity 23.04.2 installer, you know the new installer is now a Snap application right?
> 
<On testing changes>
To try out your changes for real, it is necessary to install them into an ISO. Rather than building one from scratch, it's much easier to install your version of subiquity into the daily image. Here's how to do this:

   1. Build your change into a snap:
```

    $ snapcraft snap --output subiquity_test.snap

```
   2. Grab the current version of the installer:
```

    $ urlbase=http://cdimage.ubuntu.com/ubuntu-server/daily-live/current
    $ isoname=$(distro-info -d)-live-server-$(dpkg --print-architecture).iso
    $ zsync ${urlbase}/${isoname}.zsync

```
    Run the provided script to make a copy of the downloaded installer that has your version of subiquity:
```

    $ sudo ./scripts/inject-subiquity-snap.sh ${isoname} subiquity_test.snap custom.iso

```
... <more>


---

### Post by Jaxilian on 2023-06-07
Ok so in other words, the support for LUKS encryption isn't available yet?

---

### Post by MAFoElffen on 2023-06-07
It said that it was corrected 2 months ago. If that does not work for you, like they said, then I would go to the github or launchpad and file an issue/bug. (that it still isn't workng for you.)

---

### Post by Jaxilian on 2023-06-08
> **MAFoElffen said:**
> It said that it was corrected 2 months ago. If that does not work for you, like they said, then I would go to the github or launchpad and file an issue/bug. (that it still isn't workng for you.)

thank you for help

---

