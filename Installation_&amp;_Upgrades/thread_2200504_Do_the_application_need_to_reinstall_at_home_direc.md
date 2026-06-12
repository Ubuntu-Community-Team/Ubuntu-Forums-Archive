---
title: "Do the application need to reinstall at home directory?"
date: 2014-01-19
forum: Installation &amp; Upgrades
---

### Post by ruwan2 on 2014-01-19
Hi,
Due to unrecoverable problems of my Ubuntu 12.04, 32 bit, I want to reinstall the OS. The home directory is in a separate partition. There are several applications was installed under the home directory. I would like to ask whether these applications can run after Ubuntu reinstallation? Or, some simple steps can make it possible.

Thanks,



Following is about keeping home directory I found on line:

..........................
If your /home is on a separate partition, start the installer - pick manual at the partition stage.

Select the existing / partition - Edit partition - Use as ext4,format and Mountpoint - / then save/close that window

Select the existing /home partition - Edit partition - Use as whatever  it was previously, DO NOT FORMAT and Mountpoint /home - save and close  that window

Check that the only partition that is going to be formatted is the existing / partition.

Carry on - that will install over the existing installation and use the old /home.

Use the same username though.

---

### Post by ian-weisser on 2014-01-19
If you really installed applications in your /home, then you shouldn't need to reinstall those applications.
Installing executable applications to your /home is unusual.
/home usually contains only your personal data and settings.

---

