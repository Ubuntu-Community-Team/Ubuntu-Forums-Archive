---
title: "Resuming from hibernation not working"
date: 2018-12-29
forum: MINT
---

### Post by basilky on 2018-12-29
I'm using Linux Mint but, I think this issue is not specific to Linux Mint and that's why I'm asking here.


I'm using Linux Mint 19 and it uses swap file by default instead of swap partition(I think Ubuntu 18.04 also). Everything including suspend works fine. But resume after hibernation not working.I have following configuration in my /etc/default/grub


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=38c97b08-a1d5-44b5-9e96-afca13595fe2 resume_offset=27854848"


where UUID is the root partition where swap file belongs and resume_offset is the offset of the swap file. System successfully hibernates. But on the next boot, it shows resuming from the UUID location and suddenly screen goes blank( [https://youtu.be/ZFBHNfYhuUs](https://youtu.be/ZFBHNfYhuUs) ). There is no response from the system after that.I have gone through the following threads and nothing seems to work.


[https://askubuntu.com/questions/1034185](https://askubuntu.com/questions/1034185)
[https://askubuntu.com/questions/1053134](https://askubuntu.com/questions/1053134)


Complete system details can be found at [https://termbin.com/nqpw](https://termbin.com/nqpw)


I have secure boot disabled and currently on kernel 4.18.


Does anyone have success with hibernation or any idea on why hibernation not working?

---

### Post by jeremy31 on 2018-12-29
Moved to Mint

---

