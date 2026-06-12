---
title: "Gnome-software-center: Getting rid of secure boot DBX update"
date: 2023-01-02
forum: Installation &amp; Upgrades
---

### Post by Kim Ming Yap on 2023-01-02
i see on gnome-software-center that there's this Secure Boot DBX Configuration update.
I do not want to do any update on this.
How do i get rid of this update on gnome-software-center?

Note:
Ubuntu 22.04

---

### Post by grahammechanical on 2023-01-02
The Secure Boot Database (DBX) is a list of program executables that are not safe to load. The database is maintained by Microsoft, The other year a severe security vulnerability was discovered in the Linux Boot loader (Grub). Linux distributors worked together to replace the insecure version of Grub on installed systems. They also worked with Microsoft to get the vulnerable versions of Grub blacklisted in the Secure Boot Database. This protected Linux users by preventing Linux ISO images with the vulnerable version of Grub from loading. New ISO images with the more secure version of Grub were created for all Ubuntu versions still being given security support.

My uneducated guess on what you are seeing is Microsoft and Ubuntu collaborating so that Ubuntu users can get the Secure Boot Database updated without needing to use Microsoft Windows to do it.

In this link look at post #27.

[https://answers.launchpad.net/ubuntu/+question/703205](https://answers.launchpad.net/ubuntu/+question/703205)

You can read about what was called the BootHole vulnerability and what was done to protect Linux users here:

[https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities](https://ubuntu.com/blog/mitigating-boothole-theres-a-hole-in-the-boot-cve-2020-10713-and-related-vulnerabilities)

To put things another way. Modern machines come with a feature called Secure Boot whether we like it or not. We can choose to enable or disable this feature. The secure Boot database in your machine is not up to date. Ubuntu Software if offering to correct that situation.

Regards

---

### Post by Kim Ming Yap on 2023-01-03
I understand .. issue is i am not a firmware guy and when i tried to install this DBX update i get the below error.

"Unable to update Secure Boot Dbx Configuratiokn Update: failed to write data to efivarfs: Error writing to file descriptor: Permission Denied"

i tried launching gnome-software-center using roots and still having same issue.
I am not sure which directory it is trying to write.
Maybe this has something to do with the bios having secure boot disabled (which it is).

This is too complex for me and i am just afraid i might screw things up if i were to set the bios to secure boot.
Hence i want to get rid of this secure boot dbx installation.

I don't have anything important on my linux machine.
Appreciate any advise.
Thanks.

---

