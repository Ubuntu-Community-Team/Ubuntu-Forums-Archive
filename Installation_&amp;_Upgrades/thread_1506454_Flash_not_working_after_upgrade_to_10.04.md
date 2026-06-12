---
title: "Flash not working after upgrade to 10.04"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by toddmart on 2010-06-10
I installed 10.04 today and since then, Flash will not work. First Firefox tells me that I need to install it but when I try it says that it's already installed. Synaptic also shows it as installed. Every Flash download tells me that I need to install Flash. Any ideas? I've searched the forum for similar issues but found nothing.

---

### Post by lechien73 on 2010-06-10
You will need to purge the existing installation of Flash and then reinstall from the correct repositories.

Because I had a lot of people asking me this question, I made a shell script, which will purge the old installation and install the new, after following a couple of simple initial steps. It can be downloaded [here]("http://blog.mattrudge.net/2010/05/07/installing-flash-player-from-repository-on-ubuntu-10-04-64-bit/").

I hope I'm not breaking a forum rule by linking to an outside blog post. If I am, then I apologise and will happily copy and paste the text to here.

---

### Post by toddmart on 2010-06-10
Thanks. But when I go to the other software tab, it still shows [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

No listings for Lucid partner even though Lucid shows as my installed version.

---

### Post by toddmart on 2010-06-10
I edited the 'other software' from karmic to lucid. I then reloaded and ran the terminal scripts that you suggest. It appeared to download without issue. However, I'm still getting the 'Flash Required' message ...click here to download when I go to a flash site. Any ideas?

---

### Post by bcbc on 2010-06-10
I believe you need to reinstall the restricted-extras packages following an upgrade. Also, reactivate medibuntu as these are disabled. That's all I did to get flash working again.

---

### Post by toddmart on 2010-06-11
Thanks for the reply. However, I should have disclosed that I'm a complete linux/ubuntu newbie so I'm not even sure what your reply means. I did try to refresh the update list using synaptic and get and error that it cannot find all of the repositories. That error is listed here: [http://ubuntuforums.org/showthread.php?t=1506675](http://ubuntuforums.org/showthread.php?t=1506675)

---

### Post by bcbc on 2010-06-11
Ok here are some links:
[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I don't know how to fix your other prob... but generally if you start hand editing entries you should take a backup of your sources.list in case you mess something up.

---

