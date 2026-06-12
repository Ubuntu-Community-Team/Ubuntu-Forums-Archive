---
title: "How to install 14.04.1 with random-key encrypted swap"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by treacl on 2014-10-21
Hi all,

I'm installing 14.04.1 on a new computer, trying to mimic the partition structure on my old computer, which is running 12.04. In this I have the following partitions:

/dev/sda1 = ext2 partition mapped to /boot
/dev/mapper/sda2_crypt = random-key encrypted swap space
/dev/mapper/sda3_crypt = passphrase encrypted ext4 partition mapped to /

I'm used to the alternate installer in 12.04, and I'm having trouble figuring out how to get the same results in the graphical partition editor in 14.04.1. Creating the partition table and boot partition are straightforward. But I am running into trouble when I try to create sda2_crypt for the swap space. I am following these steps:

1. Highlight "free space" & click the "+" button.
2. Select "logical volume" with type "physical volume for encryption."
3. It then creates two entries: one at "/sda2" with type "crypto," and another at "/dev/mapper/sda2_crypt" with type "ext4."
4. I highlight "/dev/mapper/sda2_crypt," click "change," and change the type to "swap."

After that, I select "free space" again, with the intent of creating the root partition in /dev/mapper/sda3_crypt. At this point, the installer throws a "fatal error," warning that my swap space is not encrypted. Huh? What am I doing wrong?

Also, how do I set the swap space to use a random key, rather than a  passphrase-protected key? This option was available in 12.04, but it  seems to be missing in 14.04.1.

Thanks,
treacl

---

