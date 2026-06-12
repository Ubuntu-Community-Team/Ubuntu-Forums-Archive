---
title: "Is it possible to reinstall Ubuntu but leave my home directory"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by stereo_steve on 2007-03-27
Hello all,

I installed Feisty Herd 5 about a week ago. It was running fine. 

I went away last weekend. When I came home last night I saw that Ubuntu was saying that I had 124 upgrades to make. I clicked ok and it began downloading. When it was installing the packages the laptop froze.

I had to take out the battery to restart the computer, its now giving me error messages. Not getting to the login screen. I think the best course of action is to just reinstall Feisty if its possible to do so and leave my home directory intact? I have important files there.

Thanks for any help I get.

Steve

---

### Post by ruibuntu on 2007-03-27
It depends on one thing, if you have your home directory in a diferent partition or not !!

If you do, it's quite easy,  just install feisty again and dont let ubuntu erase your /home. 
If it's all together,try to enter recovery mode at the grub menu.

Hope this helps!!

---

### Post by dreadlord_chris on 2007-03-27
> **stereo_steve said:**
> Hello all,

I installed Feisty Herd 5 about a week ago. It was running fine. 

I went away last weekend. When I came home last night I saw that Ubuntu was saying that I had 124 upgrades to make. I clicked ok and it began downloading. When it was installing the packages the laptop froze.

I had to take out the battery to restart the computer, its now giving me error messages. Not getting to the login screen. I think the best course of action is to just reinstall Feisty if its possible to do so and leave my home directory intact? I have important files there.

Thanks for any help I get.

Steve

If it's on a seperate partition then yes. 
If you do this then after the new install you'll need to reset the Owner/Group for it:
```

sudo chown -rH <USER>:<GROUP> /home/<USER>

```

Just replace <USER> & <GROUP> with the your login name.

---

