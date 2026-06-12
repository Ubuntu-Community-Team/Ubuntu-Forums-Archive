---
title: "install linux on completely blank brand new laptop and SSD"
date: 2022-11-26
forum: Installation &amp; Upgrades
---

### Post by genealogyxie on 2022-11-26
Is it a good idea to buy a brand new thinkpad x1 yoga gen 7, install a blank SSD on it, and use a bootable USB to install ubuntu on the computer? Or do I really need those tiny and hidden partitions that came with the original SSD?> 

---

### Post by mIk3_08 on 2022-11-27
I prefer you to "Try Ubuntu" before you decide to fully "Install Ubuntu"  so that you will find out if theirs a need for additional driver or a  proprietary driver for the machine. Regards and cheers.

---

### Post by grahammechanical on 2022-11-27
This may help you. It may be possible to find a more up to date guide on the Lenovo web site.

[https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf)

The fact is with modern computers that have a UEFI motherboard it is necessary to have what is called an EFI System Partition (ESP) because that is where the OS puts it primary boot files. Your present system will have an ESP with the Windows boot files in it. The partition should be large enough to hold also the Linux/Ubuntu boot files. The Windows boot files will not be overwritten.

If you remove the original SSD and replace it with a blank SSD then the Ubuntu installer will create all the necessary partitions including the ESP if you choose the Erase disk and install Ubuntu option. 

Do you intend to replace the original SSD in the machine? Are you want a dual boot with Windows? There is other advice we can give if that is your intention.

Regards

---

### Post by genealogyxie on 2022-11-27
> **grahammechanical said:**
> This may help you. It may be possible to find a more up to date guide on the Lenovo web site.

[https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf](https://download.lenovo.com/pccbbs/mobiles_pdf/tp_p1_gen2_ubuntu_18.04_lts_installation_v1.0.pdf)

The fact is with modern computers that have a UEFI motherboard it is necessary to have what is called an EFI System Partition (ESP) because that is where the OS puts it primary boot files. Your present system will have an ESP with the Windows boot files in it. The partition should be large enough to hold also the Linux/Ubuntu boot files. The Windows boot files will not be overwritten.

If you remove the original SSD and replace it with a blank SSD then the Ubuntu installer will create all the necessary partitions including the ESP if you choose the Erase disk and install Ubuntu option. 

Do you intend to replace the original SSD in the machine? Are you want a dual boot with Windows? There is other advice we can give if that is your intention.

Regards

I plan on taking out the original SSD and putting it in a drawer indefinitely. I don't plan on using Windows on the machine again after I install Ubuntu.

Also, does the Ubuntu full disk encryption work with the thinkpad's TPM 2.0? As I understand this, it seems like the purpose of the TPM is to prevent hackers from brute forcing your password at millions of times per second and also include compatibility with Yubikey and other smart cards for 2 factor authentication?

---

