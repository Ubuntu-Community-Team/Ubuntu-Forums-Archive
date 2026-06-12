---
title: "Installation fails with &quot;Kernel panic - not syncing: No working init found.&quot; error"
date: 2024-03-26
forum: Installation &amp; Upgrades
---

### Post by shermatovakmal on 2024-03-26
created usb installation media for Ubuntu 22.04 as described in [https://ubuntu.com/tutorials/create-a-usb-stick-on-windows:](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows:)
1. Rufus started "Run as Administrator"
2. Tried "Write in ISO image mode" and "Write in DD image mode"
3. 2 different usb drives used (16GB each)
4. Also used Etcher
5. ISO image verified using - ```
echo "45f873de9f8cb637345d6e66a583762730bbea30277ef7b32c9c3bd6700a32b2 *ubuntu-22.04.4-live-server-amd64.iso" | shasum -a 256 --check
```

But it shows some error with text "Grub" and something else for less then a second and menu is displayed. After I select "Try or install Ubuntu Server" black screen appears for some minutes and long list of errors is displayed, which ends with "Kernel panic - not syncing: No working init found. Try passing init= option to kernel

---

### Post by shermatovakmal on 2024-03-26
created new installation disk for Ubuntu 17-04.server using Rufus (ISO mode) and installation was successful.

---

### Post by ajgreeny on 2024-03-26
17.04 lost all support 6 years ago so should not be used, particularly as a server which is pointless without network access.

You must install a fully supported version so try again with 22.04 which may have suffered a faulty write to your USB used for the failed attempt to install last time.

---

### Post by ActionParsnip on 2024-03-26
Is 24.04 OK? It is due out next month. Could play ahead

---

### Post by ajgreeny on 2024-03-26
It is a possibility but the testing versions of 24.04 have not been problem free so j would suggest not yet using it as your one and only install just yet unless you are skilled enough to figure out the answers to the problems by following some of the bugs reported in the dev version section of the forum.
[https://ubuntuforums.org/forumdisplay.php?f=427](https://ubuntuforums.org/forumdisplay.php?f=427)
22.04 is pretty rock-solid in my experience using that version of Xubuntu so that is the version of server I would advise at the moment.
It still has 3 years of support remaining!

---

### Post by MAFoElffen on 2024-03-26
For 24.04 Server Edition, there was initially a problem with ssh, but that was corrected in early November. All my tests since then with Srrver Edition have been Golden.

What was not mentioned by the OP at all, is anything about what the hardware is he is trying to install to.

May be just me, but that is something I want to know before recommending anything. Especially since he only tried to install Server Edition. 

That ISO was 22.04.4 right?

---

### Post by shermatovakmal on 2024-03-27
Initially I had 22.04.1 - and it was installed/tested in VMware. So used this ISO in usb - it failed to install.
Next downloaded 22.04.4 (supposed ISO become corrupted). Same issue.
Next tried another USB drive - failed. After, tried with changing options in Rufus - no success. 
After tried Etcher - as supposed something with 16GB size and there may be some restrictions due to disk size. And Etcher prepared USB as 2GB without formatting rest space, but there was still same error.

After all, prepared 17.04 I had before, and this version installed successfully. Next, upgraded to 17.10, 18.04, 20.04. Going to upgrade to 22.04

---

### Post by zalanhari on 2024-03-27
I got the same error when I tried Tiny Core under Virtualbox (base OS: Ubuntu 24.04 LTS Noble Numbat). It worked for a while, then has gone wrong. So it is probably a general kernel problem.

---

### Post by MAFoElffen on 2024-03-27
I'm asking again... What are the hardware specs?

---

