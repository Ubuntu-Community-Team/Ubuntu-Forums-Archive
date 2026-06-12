---
title: "Custom kernel compilation errors"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by Chris_J_W on 2005-05-08
Hi, I'm trying to compile myself my own kernel coz I have some weird/different hardware, and also wanna take out a lot of stuff that's in there I don't have, and just because I want to.

At the moment I'm following the guide here: [KernelHowTo](http://www.ubuntulinux.org/wiki/KernelHowto) 

When I do the command:
make-kpkg --append-to-version=-cj.work kernel_image

The .config file is attached (gzipped coz too long to include here or attach as plaintext). 

GCC is
> 
gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)


I get the following error (in a Quote block coz I can't see any "code" tags to use here):

> 
drivers/built-in.o(.text+0x105320): In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o(.text+0x2f50): first defined here
ld: Warning: size of symbol `dump_stack' changed from 32 in arch/i386/kernel/built-in.o to 51 in drivers/built-in.o
drivers/built-in.o(.text+0x1036bf): In function `register_devices':
: undefined reference to `usb_register'
drivers/built-in.o(.text+0x103ba2): In function `loader_exit':
: undefined reference to `usb_deregister'
drivers/built-in.o(.text+0x10d1b3): In function `usb_transfer_complete_tasklet':: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d2c1): In function `usb_cancel_worker':
: undefined reference to `usb_kill_urb'
drivers/built-in.o(.text+0x10d2d0): In function `usb_cancel_worker':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d360): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_alloc_urb'
drivers/built-in.o(.text+0x10d4d7): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x10d50e): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d54e): In function `usb_bulk_or_intr_trans':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d6bc): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_alloc_urb'
drivers/built-in.o(.text+0x10d7ba): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x10d7f6): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d897): In function `usb_vendor_or_class_intf':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.text+0x10d9f3): In function `usb_select_configuration':
: undefined reference to `usb_set_interface'
drivers/built-in.o(.text+0x10da11): In function `usb_select_configuration':
: undefined reference to `usb_ifnum_to_if'
drivers/built-in.o(.text+0x10db99): In function `usb_submit_nt_urb':
: undefined reference to `usb_get_descriptor'
drivers/built-in.o(.text+0x10dc5b): In function `usb_reset_port':
: undefined reference to `usb_reset_device'
drivers/built-in.o(.text+0x10d959): In function `usb_reset_pipe':
: undefined reference to `usb_clear_halt'
drivers/built-in.o(.text+0x10fa38): In function `link_status_handler':
: undefined reference to `wireless_send_event'
drivers/built-in.o(.text+0x10fbd2): In function `link_status_handler':
: undefined reference to `wireless_send_event'
drivers/built-in.o(.text+0x1b2b59): In function `cpad_probe':
: undefined reference to `usb_set_interface'
drivers/built-in.o(.text+0x1b2eb3): In function `cpad_disconnect':
: undefined reference to `usb_unlink_urb'
drivers/built-in.o(.text+0x1b2f27): In function `cpad_disconnect':
: undefined reference to `usb_unlink_urb'
drivers/built-in.o(.text+0x1b2f32): In function `cpad_disconnect':
: undefined reference to `usb_unlink_urb'
drivers/built-in.o(.text+0x1b2fb0): In function `cpad_display_out_callback':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b305d): In function `cpad_timeout_kill':
: undefined reference to `usb_unlink_urb'
drivers/built-in.o(.text+0x1b3068): In function `cpad_timeout_kill':
: undefined reference to `usb_unlink_urb'
drivers/built-in.o(.text+0x1b30cb): In function `cpad_free_endpoint':
: undefined reference to `usb_buffer_free'
drivers/built-in.o(.text+0x1b3200): In function `cpad_setup_bulk_endpoint':
: undefined reference to `usb_buffer_alloc'
drivers/built-in.o(.text+0x1b331f): In function `cpad_setup_int_endpoint':
: undefined reference to `usb_buffer_alloc'
drivers/built-in.o(.text+0x1b357d): In function `cpad_setup_endpoints':
: undefined reference to `usb_alloc_urb'
drivers/built-in.o(.text+0x1b379f): In function `cpad_nlcd_function':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b3be2): In function `cpad_input_callback':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b3ed8): In function `cpad_submit_int_urb':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b3f45): In function `cpad_dev_add':
: undefined reference to `usb_register_dev'
drivers/built-in.o(.text+0x1b3fdd): In function `cpad_dev_remove':
: undefined reference to `usb_deregister_dev'
drivers/built-in.o(.text+0x1b4084): In function `cpad_dev_open':
: undefined reference to `usb_find_interface'
drivers/built-in.o(.text+0x1b44a4): In function `cpad_dev_write':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b46d0): In function `cpad_dev_ioctl':
: undefined reference to `usb_reset_device'
drivers/built-in.o(.text+0x1b5848): In function `cpad_fb_mmap':
: undefined reference to `remap_page_range'
drivers/built-in.o(.text+0x1b5903): In function `cpad_fb_sendurb':
: undefined reference to `usb_submit_urb'
drivers/built-in.o(.text+0x1b30dd): In function `cpad_free_endpoint':
: undefined reference to `usb_free_urb'
drivers/built-in.o(.init.text+0xc754): In function `cpad_init':
: undefined reference to `usb_register'
drivers/built-in.o(.exit.text+0x15db): In function `cpad_exit':
: undefined reference to `usb_deregister'
drivers/built-in.o(.gnu.linkonce.this_module+0xa4): undefined reference to `init_module'
drivers/built-in.o(.gnu.linkonce.this_module+0x20c): undefined reference to `cleanup_module'
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.11'
make: *** [stamp-build] Error 2
 

If anyone has any ideas what i can do to prevent this, that'd be fantastic.

-CJ

---

### Post by mirtux on 2005-05-12
Hi,
   sorry if it seems a stupid answer, do you really need that module? One time i had a similar problem, resolved just noticing that is no required by my system.... ;-)

Regards,
MC

---

### Post by az on 2005-05-12
Try using linux-tree-2.6.10 instead of the 2.6.11 source....

---

### Post by Chris_J_W on 2005-05-16
> 
do you really need that module? One time i had a similar problem, resolved just noticing that is no required by my system....


To be honest I'm not really sure - this is my work computer, and I dont know precisely what's in it, so I sort of took the shotgun approach and hope I get everything.  Also not exactly sure what module it is that's causing the error.  If it's something I don't need, I'll happily drop it...any ideas what it is?  :-k  :?: 

> 
Try using linux-tree-2.6.10 instead of the 2.6.11 source....


How does this help me? I want a custom kernel, so don't I need the source for that?  :confused:  :confused: 


Thanks...

CJ

---

### Post by mirtux on 2005-05-17
Hi,
  in trying to identify the drivers which is in question, you could try to recall the **make xconfig**, and in the "Device Drivers" section search in the right bar for *built-in.o* or something similar and then try to think if it is an useful piece...

Regards,
MC.

---

### Post by az on 2005-05-17
"How does this help me? I want a custom kernel, so don't I need the source for that?"

If you want to start from scratch, download the source from linus and configure and make it.

If you want to reconfigure your kernel, linux-tree is a good starting place.  You get all the patches and I think the default configuration is already done for you so that you do not forget anything.

---

### Post by Chris_J_W on 2005-05-20
Thanks for the help - what I've done now seems to be working after a fashion.  I grabbed the current source from kernel.org, and then more or less followed the ubuntu KernelHowTo I linked to above - that seems to be working apart from sound which I'm probably just missing a driver somewhere.  Thanks again.

---

