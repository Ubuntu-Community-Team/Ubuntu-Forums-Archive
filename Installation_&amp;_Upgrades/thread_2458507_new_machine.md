---
title: "new machine"
date: 2021-02-26
forum: Installation &amp; Upgrades
---

### Post by oneleded on 2021-02-26
i built a new machine from scratch. i'm trying to install CUDA. does it matter the order that you install. 
the first thing i did, was install the toolkit [i wasn't paying attention to the instructions], i cant help that. my machine is 64 based, an only linux, so far i only got 2 OS's, on the SSD.
i just want to know it i got to delete the toolkit, an start over. the nvidia-cuda-toolkit,  go's to cuda 10.  so i got a bit of updating to do, at least cuda 11. if that makes sense, then i am OK. hate to bother ya, if i am on the right track.
i put the HHD drive on the back burner for now. i forgot one thing,
lubuntu 20.04 has 4 desktops, i can barely take care of one. i dont need 4 desktops. the settings dont allow for removing the excess 3.

---

### Post by Frogs Hair on 2021-02-26
It might help to know what tutorial you are using . To remove the toolkit you might try the following per the Nvidia tutorial. I would think following the steps is important.

 ```
sudo /usr/local/cuda-X.Y/bin/uninstall_cuda_X.Y.pl
```

---

### Post by oneleded on 2021-02-27
[https://medium.com/@manujarvinen/setting-up-a-multi-boot-of-5-linux-distributions-ca1fcf8d502](https://medium.com/@manujarvinen/setting-up-a-multi-boot-of-5-linux-distributions-ca1fcf8d502)
this was where i started. if i dont have too delete the toolkit, i wont. i was asking before i messed up my OS, i dont know if it will. 1st., time.
i found this after i posted; [https://developer.download.nvidia.com/compute/cuda/6_5/rel/docs/CUDA_Getting_Started_Linux.pdf](https://developer.download.nvidia.com/compute/cuda/6_5/rel/docs/CUDA_Getting_Started_Linux.pdf)
is this the right guide? thanks

---

### Post by Frogs Hair on 2021-02-27
> [i found this after i posted; [https://developer.download.nvidia.co...rted_Linux.pdf]("https://developer.download.nvidia.com/compute/cuda/6_5/rel/docs/CUDA_Getting_Started_Linux.pdf")[ It appears to be the same steps and again I would say the order of the steps is important. I know completely unfamiliar with  the first tutorial, I have a simple dual boot.

---

### Post by oneleded on 2021-03-01
i didnt realize the version i had was from 2014. only 7 years behind. i need to pay more attention. maybe it's the same,... wishes,. only if they were granted.

---

