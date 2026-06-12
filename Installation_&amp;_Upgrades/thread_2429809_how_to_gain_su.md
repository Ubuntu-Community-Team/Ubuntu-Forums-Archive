---
title: "how to gain su"
date: 2019-10-23
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2019-10-23
have installed Ubuntu 18.04 by USB stick to a HP Z440 workstation almost without complaints. Unfortunately, 1st boot did not recognize network (no dhcp) nor graphics what ended with a black screen/no sync. Its a Nvidia Quadro M4000. Anyway I managed by any startup menues to enter a Desktop with VGA resolution and download the nvidia driver what is a .run file (shellscript?). To execute I open a Terminal and ls shows NIVIDIA-Linux-x86_64-352.41.run. To run it, I renamed to NVIDIA.run and tried to gain root. There was only one password entry at installation for user jv and I try

$su jv 
Passwort: ****
 
what does not complain. This gives:
$ ./NVIDIA.run
bash: ./NVIDIA.run: Permission denied

---

### Post by TheFu on 2019-10-23
All Ubuntu systems use **sudo**. Know it. Use it. Love it.  
[https://www.howtoforge.com/tutorial/sudo-beginners-guide/](https://www.howtoforge.com/tutorial/sudo-beginners-guide/)

Avoid using sudo with any GUI programs.  It is likely these programs will break things in your HOME if you choose to avoid this recommendation.

BTW, getting GPU drivers directly from some website, including the vendor, is an anti-pattern for Linux.  Use the drivers provided through the "Get additional Drivers" application.  These are tested against the Ubuntu kernels.

You'll also need to learn about file permissions. The
```
 bash: ./NVIDIA.run: Permission denied
```
error is very likely due to a permissions issue.  **chmod +x ./NVIDIA.run** will probably fix it, but you probably shouldn't be using that script.  Use the *Get additional Drivers* method instead.

---

### Post by Skaperen on 2019-10-23
even root does not get to *execute* a file unless there is an execute permission set.  it's a safety feature.

---

### Post by janvi2 on 2019-10-23
Many thanks - the graphics is fine now. Sometimes its better not to remember too many about things like the executable flag. Wont be something for the faint of heart to remcompile any libs to make them compabtible with vendors drivers. 3840x2160 booted immediately and also found some printes in the network and I hope remaining things can be solved soon

---

### Post by TheFu on 2019-10-23
> **janvi2 said:**
> Many thanks - the graphics is fine now. Sometimes its better not to remember too many about things like the executable flag. Wont be something for the faint of heart to remcompile any libs to make them compabtible with vendors drivers. 3840x2160 booted immediately and also found some printes in the network and I hope remaining things can be solved soon

If you let the "Additional Drivers" tool handle them, then relinking drivers after every kernel change is automatic and you'll get the newest, tested, GPU drivers automatically.  Some reading:
[https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its](https://www.omgubuntu.co.uk/2019/07/install-nvidia-driver-update-ubuntu-its)

Regardless, it is good form to say what you did to fix any issues AND use the "thread tools" button near the top to mark a thread as SOLVED to help the community out.

---

