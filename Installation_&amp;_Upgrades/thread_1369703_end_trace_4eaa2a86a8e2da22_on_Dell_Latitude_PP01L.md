---
title: "end trace 4eaa2a86a8e2da22 on Dell Latitude PP01L"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by florian_roger on 2010-01-01
Hi

I've install Ubuntu 8.04 on my Laptop Dell Latitude PP01L and it first worked.
But now, after Grub, I just have a black screen.
When I edit boot line to vga=normal, it shows me this error message:
> 	[<c013da48>] smp_call_function+0x1d/0x39
	[<c01109c3>] native_smp_send_stop+0x18/0x41
	[<c0123e49>] panic+0x57/0xee
	[<c0126222>] do_exit+0x52/0x694
	[<c012482a>] printk+0x14/0x18
	[<c010656c>] oops_end+0x8b/0x8f
	[<c0118f0f>] do_page_fault+0x590/0x655
	[<c016f01f>] __stab_alloc+0x2e4/0x4f2
	[<c011897f>] do_page_fault+0x0/0x655
	[<c02d1db2>] error_code+0x72/0x80
	[<c01d1545>] rb_next+0x14/0x32
	[<c01662d5>] alloc_vmap_area+0xf1/0x1a6
	[<c0166437>] __get_vm_area_node+0xad/0x135
	[<c0166517>] get_vm_area_caller+0x29/0x2e
	[<c010871c>] text_poke+0xa1/0x123
	[<c0166ac8>] vmap+0x1f/0x41
	[<c010871c>] text_poke+0xa1/0x123
	[<c018b902>] ll_rw_block+0x67/0xcc
	[<c01087d7>] alternatives_smp_unlock+0x39/0x46
	[<c03b9bf2>] alternative_instructions+0x8b/0x108
	[<c02b2d6c>] _etext+0x0/0xde494
	[<c03ba467>] check_bugs+0xd5/0xd7
	[<c03b17bc>] start_kernel+0x296/0x2a3
	---[end trace 4eaa2a86a8e2da22 ]---

Thanks for your help

---

