---
title: "Can not start virtual machine (virt-manager)"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gunksta on 2010-04-01
I created a virtual machine (Win XP), using virt-manager, as root. When I start virt-manager as a regular user, I can see my VM. Sometimes I can start the machine via virt-manager, sometimes I can't.

$USER is a member of the kvm and libvirt groups.

I feel that the machine itself is set up correctly, because I can ALWAYS start the vm with:

```
sudo kvm /var/lb/libvirt/images/WinXP.img
```

Thus, I don't know if I made a mistake or if virt-manager is doing something screwy. I don't know much about kvm/virt-manager but I am definitely enjoying it. I'd just like to get virt-manager to work correctly.

I am willing to provide additional information, test stuff out etc. Like I said - The error/problem may be sitting behind the keyboard.

---

### Post by gunksta on 2010-04-12
bump - I haven't made any progress on this, and I would like to be able to deploy virt-manager on other machines to meet different needs, but right now I am limited in my ability to do that.

---

