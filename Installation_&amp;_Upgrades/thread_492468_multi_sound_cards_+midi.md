---
title: "multi sound cards +midi"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by winston84 on 2007-07-04
I am using  ubuntu feisty and i have 2 sound cards one is an Echo Mia which after comping Alsa works
but i also have Maudio transit (usb) sound device and my midi is a mark of the Unicorn Fastlane (usb)
adapter now like I said the Mia works the Transit doesn't work and the Fastlane shows up in the Alsa
MIDI connection gui app but I can't get it to work in any of the MIDI app . Any Help would be appreciated

 Thanks Winston84

---

### Post by paulg on 2007-07-05
I can't help you with getting multiple soundcards to play nice simultaneously but I do know what should work for installing/setting up the Transit. I have a MobilePre but the install steps are basically the same for the Transit (or should be - obviously haven't tried it on a Transit myself). See the directions [here]("http://ubuntuforums.org/showthread.php?t=466667") and just choose the correct product ID and firmware name for the Transit. 

I use the command 'asoundconf' to switch between my built-in/USB soundcards. I find it works more consistently than the gui but the distro has gone through a few animals species since I last used the gui.

paul.

---

### Post by winston84 on 2007-07-05
I got the Transit work I with I know how but I compiled some much code and used so 
many commands (that I don't what they did) but it works now still can't get MIDI to work.

---

### Post by paulg on 2007-07-06
Glad the Transit is working. I did a search on google search on your Midi device. Looks like the MOTU Fastlane is supported:

[usbmidi]("http://homepage3.nifty.com/StudioBreeze/software/usbmidi-e.html")

Try:```
sudo modprobe usbmidi
```

If that does not work then you may need to download the source and compile a module which is well beyond me - but the information to do it is out there! 

Run the command above unplug the USB cable and reinsert the cable to see if it works. If it does work then you need open the file (sudo nano) /etc/modules and add a new line "usbmidi" (without quotations) to the bottom of whatever list you already have there, save and close. Now when you reboot the module will be re-loaded and you can forgo the modprobe command. Let me know how it turns out.

---

### Post by winston84 on 2007-07-07
I tried that driver but it refuse to compile . even after creating a link to my source folder
I get a  division by zero in #if and it errors out 

winston@ubuntu:~/usbmidi-20040829$ make
gcc -D__KERNEL__ -DMODULE -DLINUX -DEXPORT_SYMTAB -DREDHAT240FIX=0 -O2 -pipe -Wall -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -fno-strength-reduce -D__SMP__ -march=i686 -DMODVERSIONS -include /usr/src/linux/include/linux/modversions.h -I/usr/src/linux/include -c -o usb-midi.o usb-midi.c
cc1: error: /usr/src/linux/include/linux/modversions.h: No such file or directory
In file included from /usr/src/linux/include/asm/thread_info.h:16,
                 from /usr/src/linux/include/linux/thread_info.h:21,
                 from /usr/src/linux/include/linux/preempt.h:9,
                 from /usr/src/linux/include/linux/spinlock.h:49,
                 from /usr/src/linux/include/linux/module.h:9,
                 from usb-midi.c:46:
/usr/src/linux/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux/include/asm/processor.h:82: error: requested alignment is not a constant
/usr/src/linux/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux/include/linux/sched.h:51,
                 from /usr/src/linux/include/linux/utsname.h:35,
                 from /usr/src/linux/include/asm/elf.h:12,
                 from /usr/src/linux/include/linux/elf.h:7,
                 from /usr/src/linux/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /usr/src/linux/include/linux/sched.h:51,
                 from /usr/src/linux/include/linux/utsname.h:35,
                 from /usr/src/linux/include/asm/elf.h:12,
                 from /usr/src/linux/include/linux/elf.h:7,
                 from /usr/src/linux/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/usr/src/linux/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/usr/src/linux/include/linux/jiffies.h:274: error: for each function it appears in.)
/usr/src/linux/include/linux/jiffies.h:280:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/usr/src/linux/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:293:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:306:46: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/usr/src/linux/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/usr/src/linux/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/usr/src/linux/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/usr/src/linux/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/usr/src/linux/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /usr/src/linux/include/linux/utsname.h:35,
                 from /usr/src/linux/include/asm/elf.h:12,
                 from /usr/src/linux/include/linux/elf.h:7,
                 from /usr/src/linux/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/usr/src/linux/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/usr/src/linux/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux/include/linux/module.h:21,
                 from usb-midi.c:46:
/usr/src/linux/include/asm/module.h:62:2: error: #error unknown processor family
usb-midi.c:50:42: error: missing binary operator before token "("
usb-midi.c:53:27: error: linux/malloc.h: No such file or directory
usb-midi.c:55:27: error: linux/wrapper.h: No such file or directory
In file included from /usr/src/linux/include/linux/irq.h:22,
                 from /usr/src/linux/include/asm/hardirq.h:5,
                 from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux/include/asm/hardirq.h:5,
                 from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux/include/linux/irq.h: At top level:
/usr/src/linux/include/linux/irq.h:172: error: requested alignment is not a constant
/usr/src/linux/include/linux/irq.h:174: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /usr/src/linux/include/linux/hardirq.h:7,
                 from /usr/src/linux/include/linux/interrupt.h:11,
                 from /usr/src/linux/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux/include/asm/hardirq.h:12: error: requested alignment is not a constant
In file included from /usr/src/linux/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux/include/linux/interrupt.h: In function ‘cli’:
/usr/src/linux/include/linux/interrupt.h:204: warning: implicit declaration of function ‘local_irq_disable’
/usr/src/linux/include/linux/interrupt.h: In function ‘sti’:
/usr/src/linux/include/linux/interrupt.h:208: warning: implicit declaration of function ‘local_irq_enable’
/usr/src/linux/include/linux/interrupt.h: In function ‘save_flags’:
/usr/src/linux/include/linux/interrupt.h:212: warning: implicit declaration of function ‘local_save_flags’
In file included from usb-midi.c:65:
usb-midi.h:160:41: error: missing binary operator before token "("
usb-midi.c: At top level:
usb-midi.c:85: error: expected ‘)’ before string constant
usb-midi.c:89: error: expected ‘)’ before string constant
usb-midi.c:93: error: expected ‘)’ before string constant
usb-midi.c:97: error: expected ‘)’ before string constant
usb-midi.c:101: error: expected ‘)’ before string constant
usb-midi.c:105: error: expected ‘)’ before string constant
usb-midi.c:109: error: expected ‘)’ before string constant
usb-midi.c:113: error: expected ‘)’ before string constant
usb-midi.c:117: error: expected ‘)’ before string constant
usb-midi.c:125: error: expected ‘)’ before string constant
usb-midi.c:130:42: error: missing binary operator before token "("
usb-midi.c: In function ‘usb_write’:
usb-midi.c:360: warning: implicit declaration of function ‘FILL_BULK_URB’
usb-midi.c:363: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c:441:41: error: missing binary operator before token "("
usb-midi.c: In function ‘usb_bulk_read’:
usb-midi.c:444: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c: In function ‘usb_midi_open’:
usb-midi.c:936: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c:970: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
usb-midi.c: In function ‘usb_midi_release’:
usb-midi.c:1028: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
usb-midi.c: In function ‘alloc_midi_in_endpoint’:
usb-midi.c:1085: error: too few arguments to function ‘usb_alloc_urb’
usb-midi.c: In function ‘alloc_midi_out_endpoint’:
usb-midi.c:1152: error: too few arguments to function ‘usb_alloc_urb’
usb-midi.c: In function ‘get_alt_setting’:
usb-midi.c:1578: error: request for member ‘num_altsetting’ in something not a structure or union
usb-midi.c:1581: error: request for member ‘altsetting’ in something not a structure or union
usb-midi.c:1586: error: ‘struct usb_interface_descriptor’ has no member named ‘endpoint’
usb-midi.c: In function ‘alloc_usb_midi_device’:
usb-midi.c:1784: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c: In function ‘detect_yamaha_device’:
usb-midi.c:1846: warning: initialization from incompatible pointer type
usb-midi.c:1859: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1860: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1875: warning: comparison of distinct pointer types lacks a cast
usb-midi.c:1885: warning: implicit declaration of function ‘usb_set_configuration’
usb-midi.c: In function ‘detect_midi_subclass’:
usb-midi.c:1960: warning: initialization from incompatible pointer type
usb-midi.c:1969: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1970: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1985: warning: comparison of distinct pointer types lacks a cast
usb-midi.c:2088:42: error: missing binary operator before token "("
usb-midi.c: At top level:
usb-midi.c:2168: warning: initialization from incompatible pointer type
usb-midi.c:2169: warning: initialization from incompatible pointer type
usb-midi.c:2170:42: error: missing binary operator before token "("
usb-midi.c:2173: error: unknown field ‘driver_list’ specified in initializer
usb-midi.c:2173: warning: braces around scalar initializer
usb-midi.c:2173: warning: (near initialization for ‘usb_midi_driver.ioctl’)
usb-midi.c:2173: error: ‘struct usb_driver’ has no member named ‘driver_list’
usb-midi.c:2173: error: ‘struct usb_driver’ has no member named ‘driver_list’
usb-midi.c:2173: warning: excess elements in scalar initializer
usb-midi.c:2173: warning: (near initialization for ‘usb_midi_driver.ioctl’)
make: *** [usb-midi.o] Error 1
winston@ubuntu:~/usbmidi-20040829$

---

### Post by paulg on 2007-07-09
Do you have the kernel headers installed? If so, do you have the kernel source installed?

I assume you installed the packages included in the 'build-essential' as make is at least running. Try with the headers first and try with the source after. It seems to be looking for source headers that aren't on your system. I don't have any experience with compiling modules unfortunately...

---

