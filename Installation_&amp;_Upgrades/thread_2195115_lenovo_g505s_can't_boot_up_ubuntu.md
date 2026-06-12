---
title: "lenovo g505s can't boot up ubuntu"
date: 2013-12-22
forum: Installation &amp; Upgrades
---

### Post by shubh9835 on 2013-12-22
i have this laptop named lenovo g505s

[http://www.flipkart.com/lenovo-essential-g505s-59-380146-laptop-apu-quad-core-a10-8gb-1tb-dos-2-5gb-graph/p/itmdm79dbkjzewwk?pid=COMDM799ZGJTXAVT&otracker=from-search&srno=t_1&query=lenovo+g505s&ref=74b0fb2f-800c-4120-a422-70ef28b6c8cc](http://www.flipkart.com/lenovo-essential-g505s-59-380146-laptop-apu-quad-core-a10-8gb-1tb-dos-2-5gb-graph/p/itmdm79dbkjzewwk?pid=COMDM799ZGJTXAVT&otracker=from-search&srno=t_1&query=lenovo+g505s&ref=74b0fb2f-800c-4120-a422-70ef28b6c8cc)

amd a10
8gb ram
2.5gb graphics
1tb hdd

i downloaded ubuntu 13.10 and put it in a usb. the live usb worked perfectly fine with no issues. after i installed it, when i restarted i get this purple screen and nothing happens.
i tried to hold shift yet grub menu dosen't come up.

i am trying to make a dual boot windows 8 and ubuntu. had same problems with ubuntu 12.04 & 13.04.

i could install ubuntu under virtualbox previously.

don't know what's wrong.
even my windows won't boot up.

had set 4gb swap area, 32gb root and 512mb for boot

help!!:(

---

### Post by oldfred on 2013-12-23
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Do not attempt to reinstall Ubuntu except with Something Else. Users are reinstalling Ubuntu and it only shows Ubuntu and they think it will only overwrite the Ubuntu install. If it does now show the Windows then it totally erases drive. Not sure if just user error, installer bug, or Windows reverts to hibernation or fast boot and then the installer cannot see Windows so just assumes you want to install to entire drive.

---

### Post by shubh9835 on 2013-12-28
> **oldfred said:**
> Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

Do not attempt to reinstall Ubuntu except with Something Else. Users are reinstalling Ubuntu and it only shows Ubuntu and they think it will only overwrite the Ubuntu install. If it does now show the Windows then it totally erases drive. Not sure if just user error, installer bug, or Windows reverts to hibernation or fast boot and then the installer cannot see Windows so just assumes you want to install to entire drive.

hi! i could fix the problem. i don't know exactly how but i managed to set up a dual boot. what i did in the bios was

boot- legacy first
graphics- UMA      (i have switchable graphics)

---

### Post by harsh.sanghvi86 on 2014-01-11
hey, thanks a lot .. i was facing the same issue, initially i thought something went wrong with the installation, but when the issue persisted the second time, your fix helped.

---

### Post by harsh.sanghvi86 on 2014-01-11
hey shubh, i replied too early, it seems that the fix ain't working anymore. I am trying to make my system dual boot, is this the reason. I installed windows 8 first & then ubuntu 12.04. sometimes it boots sometimes it doesn't & show the blank screen with ubuntu back colours. can you please let me know, is it hardware issue or something else?

---

### Post by shubh9835 on 2014-06-03
hey harsh.sanghvi86  after my installation started working, as soon as i switched to switchable graphics, boom ubuntu won't boot up again. 
i installed fedora 20 and it worked for me. :)

---

### Post by shubh9835 on 2014-12-09
Ok i think i found the solution.. seems unity desktop is not compatible with our system. Kbuntu should work fine... i tried the gnome as well as kde version of fedora and they worked for me

---

