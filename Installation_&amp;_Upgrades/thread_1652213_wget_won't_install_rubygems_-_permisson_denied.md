---
title: "wget won't install rubygems - permisson denied"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by fastveg on 2010-12-24
> wget [http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz](http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz)

> --2010-12-24 08:41:19--  [http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz](http://rubyforge.org/frs/download.php/70696/rubygems-1.3.7.tgz)
Resolving rubyforge.org... 205.234.109.19
Connecting to rubyforge.org|205.234.109.19|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://files.rubyforge.vm.bytemark.co.uk/rubygems/rubygems-1.3.7.tgz](http://files.rubyforge.vm.bytemark.co.uk/rubygems/rubygems-1.3.7.tgz) [following]
--2010-12-24 08:41:19--  [http://files.rubyforge.vm.bytemark.co.uk/rubygems/rubygems-1.3.7.tgz](http://files.rubyforge.vm.bytemark.co.uk/rubygems/rubygems-1.3.7.tgz)
Resolving files.rubyforge.vm.bytemark.co.uk... 80.68.94.54
Connecting to files.rubyforge.vm.bytemark.co.uk|80.68.94.54|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 290986 (284K) [application/x-gzip]
rubygems-1.3.7.tgz: Permission denied

Cannot write to `rubygems-1.3.7.tgz' (Permission denied).

Any ideas why this would be happening?

---

### Post by dino99 on 2010-12-24
why not using apt-get ?

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

---

### Post by oldos2er on 2010-12-24
> **fastveg said:**
> Any ideas why this would be happening?

You're running the command somewhere outside your home folder?

---

### Post by fastveg on 2010-12-24
I ended up fixing this by logging in as root.  Well, sort of.  Things are still broken.

That being said, could you expand on your answer oldos2er?  What is the significance of the home folder?

---

### Post by oldos2er on 2010-12-25
Your home folder is where all your user's data and config files are kept. You (i.e. your user) should have full read/write permissions in your home folder. If you want to have write permissions outside of your home folder, you need admin privileges which you can get in terminal using **sudo**, or graphically using **gksudo**.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm)

[https://help.ubuntu.com/community/HomeFolder](https://help.ubuntu.com/community/HomeFolder)

---

