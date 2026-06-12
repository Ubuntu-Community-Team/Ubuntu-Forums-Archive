---
title: "Help with Make Install"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by glomboi on 2010-06-13
Hi, I get the following output when trying to compile and install the driver for the EyeToy webcam ([see here]("http://magentasmelange.wikidot.com/eyetoyinskype"))
Can you please help me to dignose the problem?
```
tony_glombek@Glombook:~/Downloads/ov51x-jpeg-1.5.9$ sudo make install
[sudo] password for tony_glombek: 
make -C /lib/modules/2.6.32-22-generic/build M=/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘create_proc_ov511_cam’:
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:677: error: implicit declaration of function ‘info’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:681: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:689: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:700: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:712: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘proc_ov511_create’:
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:766: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_clear_snapshot’:
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:1691: error: implicit declaration of function ‘warn’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: In function ‘ov51x_v4l1_ioctl’:
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 1 of ‘video_usercopy’ from incompatible pointer type
include/media/v4l2-ioctl.h:298: note: expected ‘struct file *’ but argument is of type ‘struct inode *’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 2 of ‘video_usercopy’ makes integer from pointer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘unsigned int’ but argument is of type ‘struct file *’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: warning: passing argument 4 of ‘video_usercopy’ makes pointer from integer without a cast
include/media/v4l2-ioctl.h:298: note: expected ‘v4l2_kioctl’ but argument is of type ‘long unsigned int’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6386: error: too many arguments to function ‘video_usercopy’
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c: At top level:
/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.c:6651: warning: initialization from incompatible pointer type
make[2]: *** [/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9/ov51x-jpeg-core.o] Error 1
make[1]: *** [_module_/home/tony_glombek/Downloads/ov51x-jpeg-1.5.9] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [all] Error 2
```

I have Googled lots of bits but am really struggling to find solutions.
Also, if it helps, I followed a tutorial here: [http://ubuntuforums.org/showthread.php?t=1448394](http://ubuntuforums.org/showthread.php?t=1448394) since the user there seemed to have a similar problem.

Thanks in advance!

---

### Post by glomboi on 2010-06-13
Also, how do I change the location of this thread, I realise "Installation & Upgrades" is the wrong topic for this to go under. Sorry!

---

