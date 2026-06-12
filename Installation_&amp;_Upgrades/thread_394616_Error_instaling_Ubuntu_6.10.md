---
title: "Error instaling Ubuntu 6.10"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by bataya on 2007-03-27
I`m try to install Ubuntu 6.10, and every time I get this error message > [17179570.540000] 0804111 c0166b94 dffee 080 0084111 dfc05034 0000000 00000000

[17179570.540000] Call trace

[17179570.540000] alloc_pid+0x1ab/0x270 <c012164d> do_fork+0x7d/0x200

[17179570.540000] <c010143e> kernel_thread+0x8e0xb0 <c0132450> ___call_usermodehelper+0x0/0x10

[17179570.540000] <c001322d9> ___call_usermodehelper+0x39/0x50 <c0132702> run_workqueue+0x72/0xf0

[17179570.540000] <01322a0> ___call_usermodehelpe+0x0/0x50 <c0133207> worker_therad+0x177/0x140

[17179570.540000] kthread+0xab/0xe0 <c0133207> kthread+0x0/0xe0

[17179570.540000] Code: ff ff ff ff c7 43 14 00 00 00 00 8b 44 24 85 c0 74 01 fa 8b 44 24 08 c8 ad 39 17 00 8b 44 24 20 83 c0 18 8b 50 04 84 03 85 58 04 <89> 1a 89 53 04 8b 4c 24 20 8b 42 38 01 41 18 b8 01

[17179570.540000] EIP: [<c0167042>] cache_alloc_refill+0x540 SS:ESP 0068:ef114bd0s

[17179570.540000] I try diferent CD, and every time error. my configuration Barton 3000+, 768 mb ram, hdd maxtor 80 gb, MSI via kt600 and radeon 9200
P.S. Sory for my bad english

---

