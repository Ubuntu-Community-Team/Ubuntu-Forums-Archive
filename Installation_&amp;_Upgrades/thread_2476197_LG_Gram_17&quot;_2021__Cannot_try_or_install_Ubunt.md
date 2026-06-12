---
title: "LG Gram 17&quot; 2021:  Cannot try or install Ubuntu 20.04 LTS"
date: 2022-06-19
forum: Installation &amp; Upgrades
---

### Post by uggitt2 on 2022-06-19
Hi, I am trying to try/Install Ubuntu 20.04 LTS  & 22.04 LTS but I am getting the following errors as shown in the link below

[https://postimg.cc/vDp5Ds46](https://postimg.cc/vDp5Ds46)

Laptop Specs:  Intel Core i7 (11th Gen), 16GB RAM, 1TB NVME (Windows 11), 1TB NVME (For Linux)

I have tried disabling secure boot and changed the TPM version to TPM2 from fTPM as menioned in a couple of posts I have found.

Would  be grateful if anyone has any ideas of other BIOS settings or what the  errors mean so I can get Ubuntu installed as I need it for work.

Arch and Fedora distros work and boot up from USB drives I have created.

Regards

Mark

---

### Post by tea for one on 2022-06-19
11th Gen Intel Processor would probably need a later kernel than the one in 20.04.
Have you tried Ubuntu 22.04?

---

### Post by uggitt2 on 2022-06-19
Thanks for the reply, I have actually tried with 22.04 and 20.4.

Same errors.

Mark

---

### Post by tea for one on 2022-06-19
Have you disabled TPM?

By the way, many users (including myself) may not be able to view your google drive link.
Can you post the image as an attachment in your next reply.

---

### Post by grahammechanical on 2022-06-19
I cannot access the image in that Google account because I do not have a Google account. And I am not sad about that.

I have an Intel i7 CPU. It runs Ubuntu 20.04 without any problem. The laptop also has a Trusted Platform Module but the machine came with only Ubuntu 20.04 installed. So, Windows has not taken ownership of the TPM. What evidence do you have that Windows is blocking the installation of non-Windows operating systems?

Regards

---

### Post by uggitt2 on 2022-06-19
Here is another link to the screenshot as I am unable to paste it in to the message in the forum

[URL="https://postimg.cc/vDp5Ds46"]https://postimg.cc/vDp5Ds46

Mark
[/URL]

---

### Post by yancek on 2022-06-19
Use the paper clip icon in the top row (right) of icons when you are posting a reply to attach something.
You link seems to show problems with ACPI but I have no suggestions on what to try.  Might do an online search "ACPI problems ubuntu" or similar.

---

### Post by ubfan1 on 2022-06-20
Forget the ACPI messages, see the "unable to mount root" answers: 
[https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0](https://askubuntu.com/questions/41930/kernel-panic-not-syncing-vfs-unable-to-mount-root-fs-on-unknown-block0-0)

---

