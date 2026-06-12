---
title: "How do I bring /usr (Karmic) not on it's own partition to a Clean install of Lucid?"
date: 2010-01-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mikodo on 2010-01-12
I have Karmic's /home on a separate partition and intend to bring it forward to a Lucid's /home partition during a clean install. 

How can I bring forward the contents of /usr, which is not in it's own partition in Karmic, to a new /usr partition in Lucid?

I want to bring forward app's I have installed, that are not officially part of Ubuntu's respositories and not have to do a lot of reconfigurations after installing Lucid.

Can I just backup the contents of Karmic's /usr, say to an External USB HD, and during the clean install of Lucid, with a newly created /usr partition, bring the contents of Karmic's /usr into it from the backup?

Or, is there an easier way to complete this?

Thank you.

---

### Post by J V on 2010-01-12
dont do that, the bloat would be INCREDIBLE!

I write small shell scripts myself, I install skype, download only gedit plugins, and a bunch of others automatically and get the latest versions all by running a script...

Learn bash, its not hard :)

just like so:
```
wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64
sudo gdebi "skype-ubuntu*.deb"
```

---

### Post by mikodo on 2010-01-12
> **J V said:**
> dont do that, the bloat would be INCREDIBLE!

I write small shell scripts myself, I install skype, download only gedit plugins, and a bunch of others automatically and get the latest versions all by running a script...

Learn bash, its not hard :)

just like so:
```
wget http://www.skype.com/go/getskype-linux-beta-ubuntu-64
sudo gdebi "skype-ubuntu*.deb"
```

Thanks for the information and advice.

I guess I wait until I have gained the knowledge in bash.

Mike

---

