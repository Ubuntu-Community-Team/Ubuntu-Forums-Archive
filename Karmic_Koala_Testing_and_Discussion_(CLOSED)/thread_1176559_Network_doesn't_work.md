---
title: "Network doesn't work"
date: 2009-06-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by skeve on 2009-06-02
Recently I installed Karmic Koala and now both wired and wireless network connection doesn't work. The same goes with the kernels  2.6.30-6 (from the main repository) and 2.6.30-020630rc7 (from the mainline ppa), while 2.6.30-020630rc3 still works. 
What could be the problem?

Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

/var/log/messages contains
iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks                                  
iwl3945: Copyright(c) 2003-2009 Intel Corporation                                                                        
iwl3945 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                         
iwl3945 0000:05:00.0: BAR 0: can't reserve mem region [0xfddff000-0xfddfffff]                                            
iwl3945 0000:05:00.0: PCI INT A disabled                                                                                 
iwl3945: probe of 0000:05:00.0 failed with error -16                             


And no sound, by the way:
HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                                       
HDA Intel 0000:00:1b.0: BAR 0: can't reserve mem region [0xfe138000-0xfe13bfff]                                          
HDA Intel 0000:00:1b.0: PCI INT A disabled                                                                               
HDA Intel: probe of 0000:00:1b.0 failed with error -16

---

### Post by skeve on 2009-06-03
So noone see this error? :(
I upgraded from Jaunty Jackalope, if that matters.
It seems to me that the main problem is here: "probe of ... failed with error -16 "
And the strange thing is that the old kernel works while the new one doesn't.
I would appreciate an advice!

---

### Post by hexsel on 2009-06-03
there's another thread about wireless and nvidia, the latest kernel apparently doesn't have the restricted drivers modules uploaded

---

### Post by skeve on 2009-06-04
Thanks! But I'm not so sure about that. I tested kernels from mainline ppa and the thing is that 2.6.30-rc3 works while 2.6.30-rc7 doesn't. Are you sure it may be connected with the restricted modules?

---

