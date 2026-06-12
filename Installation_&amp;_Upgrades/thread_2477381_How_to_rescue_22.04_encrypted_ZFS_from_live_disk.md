---
title: "How to rescue 22.04 encrypted ZFS from live disk?"
date: 2022-07-23
forum: Installation &amp; Upgrades
---

### Post by libertyspike138 on 2022-07-23
I have been using Ubuntu since ver. 6. I have been using ZFS on my server for storage for many years but never on the / drive. I noticed that with 22.04 that encrypting the home directory has apparently been deprecated due to vulnerabilities. Now you have to select whole drive encryption with either LVM or ZFS in 22.04 setup. I chose ZFS considering I'm more familiar with it but this concerns me because if the system breaks or I need to rescue data off of the drive I cannot access it from a live environment. I have read through several man pages and at one point had a volume mounted with system.key available but could not get it to load it. Is anybody familiar with any good tutorials on mounting encrypted ZFS on rpool & bpool from a live environment to fix the system or rescue data? I'm not sure if LVM which I'm not too familiar with would be any easier. I'm open to suggestions.

---

### Post by libertyspike138 on 2022-07-23
I was trying to do this to mount it but when I get to "zfs load-key -a" I end up with an error stating it was unable to load, no such file or directory, 0 of 1 keys loaded.
[https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#rescuing-using-a-live-cd](https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2022.04%20Root%20on%20ZFS.html#rescuing-using-a-live-cd)

---

### Post by libertyspike138 on 2022-07-23
Solved by using the example in the url above but by replacing "zfs load-key -a" with "zfs load-key -L file:///media/ubuntu/keystore-rpool/system.key rpool".

---

### Post by libertyspike138 on 2022-07-23
Looks like I spoke too soon. While I was able to load the key and import and mount my rpool & bpool there is still an issue. All of the directory structure looks fine but there are no files in the folders.

---

### Post by libertyspike138 on 2022-07-23
Disregard the last post. This is a new install without any user files on it just yet but I was looking for some familiar files that have since been moved to another location in this release. I'm pretty sure this should be a usable scenario in order to rescue data in the event of a failure.

---

