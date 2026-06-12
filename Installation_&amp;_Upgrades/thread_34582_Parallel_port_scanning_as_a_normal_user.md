---
title: "Parallel port scanning as a normal user ?"
date: 2005-05-15
forum: Installation &amp; Upgrades
---

### Post by Jellus on 2005-05-15
Hi all,

I discovered that to get my parallel port scanner recognised i have to do modprobe ppdev first ...
I can only use Xsane as root for now by the way ... but there are ways to fix this i have read although i dont know how to do it yet ...
if anybody can help me here please do .. also i would like to put modprobe ppdev in a startup script or so ... can anybody tell me where i should do this ... and how ...

greetings,

Jellus

**I got this answer in reply:**

You should be able to go into the system menu and open up the users/groups manager. It should ask for your password, and then find your username and double click it. Choose the tab on the far right (groups or permissions or something) and put yourself into the scanner group. (you will need to log out and back in for this to take effect)

then use the following command: sudo gedit /etc/modules and add ppdev to the bottom of the list.

Sorry for being vague, but I happen to be in windows right now (video editing), so I can't be precise. If you run into trouble, or can't find something i've mentioned, just post here again, and I should be in Ubuntu by then 


**I tried to make it work on the basis of this answer:**


Hi ming0,

I have done what you said ... lets see what happens ...
I am rebooting as i am typing now ... typing on another linux box
in case you are wondering ...
After rebooting ... doing
as root user sane-find-scanner -p .. i am able to find my mustek scanner ....
so it works ...
Thanx lots for helping me out with this ...

My next problem is getting it to work as a normal user ....

reading up on the matter ... i found out that there are two ways ..
1) using libieee1284
2) using saned

It also says the first method, i.e. using libieee1284 is preferred ...

If anybody can help me out with this .. please do ..
It would help me a lot ...

Greetings,

Jellus

---

### Post by Jellus on 2005-05-21
Hi all,

i would like to post my solution ... to the problems i have been having ... being unable to scan as a normal user .. i enabled ppdev ... previously ... enabling me to scan as root user ... i also found out that support for libieee1284 is enabled by default by ubuntu ... which you can find out by doing

ldd `which sane-find-scanner` | grep libieee1284

If this doesn't produce any output, you don't have support for it. 
To check whether you don't have enough access rights or your scanner is not recognized at all, run

          $ SANE_DEBUG_SANEI_PA4S2=128 scanimage -L
     
 The output of this command might be several pages long. You should scan the output for one of those lines:

    * If you don't have support for libieee1284 nor for direct parralel port operations, you should find a line like this:

          [sanei_pa4s2] sanei_pa4s2_devices: A4S2 support not compiled
        

      or

          [sanei_pa4s2] sanei_pa4s2_open: A4S2 support not compiled
        
    * If you find a line like this

            [sanei_pa4s2] pa4s2_init: 0 ports reported by IEEE 1284 library
      
      or like this

            [sanei_pa4s2] pa4s2_open: could not open device `parport0` (Error initializing port)
          
      you probably do not have support for parallel port devices enabled in your kernel.

    * If you find a line like

            [sanei_pa4s2] pa4s2_open: `0x378` is not a valid device name
          

      or

            [sanei_pa4s2] pa4s2_open: `parport0` is not valid port number        

      you probably gave the wrong device name in your mustek_pp.conf. You should use * as device name to auto-detect your scanner's port.

None of these errors occur in my case ... i will put my output here so you can see whats happening ...

**************** BEGIN OUTPUT ****************************************************

root@ubuntu:/dev # SANE_DEBUG_SANEI_PA4S2=128 scanimage -L
[sanei_debug] Setting debug level of sanei_pa4s2 to 128.
[sanei_pa4s2] sanei_pa4s2: interface called for the first time
[sanei_pa4s2] sanei_pa4s2_open: called for device 'parport0'
[sanei_pa4s2] sanei_pa4s2_open: trying to connect to port
[sanei_pa4s2] pa4s2_open: trying to attach dev `parport0`
[sanei_pa4s2] pa4s2_init: static int first_time = 1
[sanei_pa4s2] pa4s2_init: called for the first time
[sanei_pa4s2] pa4s2_init: initializing libieee1284
[sanei_pa4s2] pa4s2_init: 1 ports reported by IEEE 1284 library
[sanei_pa4s2] pa4s2_init: port 0 is `parport0`
[sanei_pa4s2] pa4s2_init: allocating port list
[sanei_pa4s2] pa4s2_init: initialized successfully
[sanei_pa4s2] pa4s2_open: looking up port in list
[sanei_pa4s2] pa4s2_open: port is in list at port[0]
[sanei_pa4s2] pa4s2_open: setting up port data
[sanei_pa4s2] pa4s2_open: name=parport0 in_use=SANE_TRUE
[sanei_pa4s2] pa4s2_open: enabled=SANE_FALSE mode=PA4S2_MODE_NIB
[sanei_pa4s2] pa4s2_open: opening device
[sanei_pa4s2] pa4s2_open: device `parport0` opened...
[sanei_pa4s2] pa4s2_open: returning SANE_STATUS_GOOD
[sanei_pa4s2] pa4s2_open: open dev `parport0` as fd 0
[sanei_pa4s2] sanei_pa4s2_open: connected to device using fd 0
[sanei_pa4s2] sanei_pa4s2_open: checking for scanner
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 1
[sanei_pa4s2] sanei_pa4s2_enable: enable port 'parport0'
[sanei_pa4s2] pa4s2_enable: prelock[] = {0x04, 0x80, 0x0c}
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_open: reading ASIC id
[sanei_pa4s2] sanei_pa4s2_readbegin: called for fd 0 and register 0
[sanei_pa4s2] sanei_pa4s2_readbegin: NIB readbegin
[sanei_pa4s2] pa4s2_readbegin_nib: selecting register 0 at 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbegin: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbyte: called with fd 0
[sanei_pa4s2] sanei_pa4s2_readbyte: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readbyte: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readbyte: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readbyte: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readbyte: read in NIB mode
[sanei_pa4s2] pa4s2_readbyte_nib: reading value 0xa5 from 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbyte: read finished
[sanei_pa4s2] sanei_pa4s2_readbyte: got value 0xa5
[sanei_pa4s2] sanei_pa4s2_readbyte: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readend: called for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readend: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readend: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readend: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readend: NIB mode readend
[sanei_pa4s2] pa4s2_readend_nib: end of reading sequence for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_open: detected ASIC id 1015
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 0
[sanei_pa4s2] sanei_pa4s2_enable: disable port 'parport0'
[sanei_pa4s2] pa4s2_disable: state restored
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_open: trying better modes
[sanei_pa4s2] sanei_pa4s2_open: trying mode 0
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 1
[sanei_pa4s2] sanei_pa4s2_enable: enable port 'parport0'
[sanei_pa4s2] pa4s2_enable: prelock[] = {0x04, 0x80, 0x0c}
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbegin: called for fd 0 and register 0
[sanei_pa4s2] sanei_pa4s2_readbegin: NIB readbegin
[sanei_pa4s2] pa4s2_readbegin_nib: selecting register 0 at 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbegin: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbyte: called with fd 0
[sanei_pa4s2] sanei_pa4s2_readbyte: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readbyte: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readbyte: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readbyte: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readbyte: read in NIB mode
[sanei_pa4s2] pa4s2_readbyte_nib: reading value 0xa5 from 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbyte: read finished
[sanei_pa4s2] sanei_pa4s2_readbyte: got value 0xa5
[sanei_pa4s2] sanei_pa4s2_readbyte: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readend: called for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readend: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readend: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readend: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readend: NIB mode readend
[sanei_pa4s2] pa4s2_readend_nib: end of reading sequence for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 0
[sanei_pa4s2] sanei_pa4s2_enable: disable port 'parport0'
[sanei_pa4s2] pa4s2_disable: state restored
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_open: mode works
[sanei_pa4s2] sanei_pa4s2_open: skipping mode UNI
[sanei_pa4s2] sanei_pa4s2_open: trying mode 2
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 1
[sanei_pa4s2] sanei_pa4s2_enable: enable port 'parport0'
[sanei_pa4s2] pa4s2_enable: prelock[] = {0x04, 0x80, 0x0c}
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbegin: called for fd 0 and register 0
[sanei_pa4s2] sanei_pa4s2_readbegin: EPP readbegin
[sanei_pa4s2] pa4s2_readbegin_epp: selecting register 0 at 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbegin: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbyte: called with fd 0
[sanei_pa4s2] sanei_pa4s2_readbyte: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readbyte: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readbyte: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readbyte: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readbyte: read in EPP mode
[sanei_pa4s2] pa4s2_readbyte_epp: reading value 0xa5 from 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbyte: read finished
[sanei_pa4s2] sanei_pa4s2_readbyte: got value 0xa5
[sanei_pa4s2] sanei_pa4s2_readbyte: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readend: called for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readend: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readend: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readend: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readend: EPP mode readend
[sanei_pa4s2] pa4s2_readend_epp: end of reading sequence
[sanei_pa4s2] sanei_pa4s2_readend: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 0
[sanei_pa4s2] sanei_pa4s2_enable: disable port 'parport0'
[sanei_pa4s2] pa4s2_disable: state restored
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_open: mode works
[sanei_pa4s2] sanei_pa4s2_open: using mode 2
[sanei_pa4s2] sanei_pa4s2_open: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 1
[sanei_pa4s2] sanei_pa4s2_enable: enable port 'parport0'
[sanei_pa4s2] pa4s2_enable: prelock[] = {0x04, 0x80, 0x0c}
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbegin: called for fd 0 and register 0
[sanei_pa4s2] sanei_pa4s2_readbegin: EPP readbegin
[sanei_pa4s2] pa4s2_readbegin_epp: selecting register 0 at 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbegin: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readbyte: called with fd 0
[sanei_pa4s2] sanei_pa4s2_readbyte: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readbyte: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readbyte: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readbyte: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readbyte: read in EPP mode
[sanei_pa4s2] pa4s2_readbyte_epp: reading value 0xa5 from 'parport0'
[sanei_pa4s2] sanei_pa4s2_readbyte: read finished
[sanei_pa4s2] sanei_pa4s2_readbyte: got value 0xa5
[sanei_pa4s2] sanei_pa4s2_readbyte: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_readend: called for fd 0
[sanei_pa4s2] sanei_pa4s2_readend: we hope, the backend called
[sanei_pa4s2] sanei_pa4s2_readend: readbegin, so the port is ok...
[sanei_pa4s2] sanei_pa4s2_readend: this means, I did not check it - it's
[sanei_pa4s2] sanei_pa4s2_readend: not my fault, if your PC burns down.
[sanei_pa4s2] sanei_pa4s2_readend: EPP mode readend
[sanei_pa4s2] pa4s2_readend_epp: end of reading sequence
[sanei_pa4s2] sanei_pa4s2_readend: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_enable: called for fd 0 with value 0
[sanei_pa4s2] sanei_pa4s2_enable: disable port 'parport0'
[sanei_pa4s2] pa4s2_disable: state restored
[sanei_pa4s2] sanei_pa4s2_enable: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_close: fd = 0
[sanei_pa4s2] sanei_pa4s2_close: freeing resources
[sanei_pa4s2] pa4s2_close: fd=0
[sanei_pa4s2] pa4s2_close: this is port 'parport0'
[sanei_pa4s2] pa4s2_close: checking whether port is enabled
[sanei_pa4s2] pa4s2_close: trying to free io port
[sanei_pa4s2] pa4s2_close: marking port as unused
[sanei_pa4s2] pa4s2_close: returning SANE_STATUS_GOOD
[sanei_pa4s2] sanei_pa4s2_close: finished
device `mustek_pp:Mustek-1200CP' is a Mustek 1200CP flatbed scanner

************* END OUTPUT ************************************************

As you can see i dont have any of the errors mentioned above ...

      If you have support for parallel port devices, you probably don't have enough access rights to the parallel port device:

            $ ls -l /dev/parport0
          

      Make sure you have read/write access to this device, i.e. either
          o you own it and it's read/writeable for you
          o you are in the group owning the device and it's read/writeable for the group
          o the device is read/writeable for everybody (insecure)
      Please make sure, you have CONFIG_PPDEV enabled in your kernel's configuration. To check whether you have parallel port device support enabled, try

            $ ls -l /dev/parport*
          
      This command should show a lot of character devices, all looking something like this:

            crw-rw----  1 root root 99,  0 Jan  1  1970 /dev/parport0
          

      You can create such a device using this command:

            # mknod /dev/parport0 c 99 0
          

In my case after doing this ... i get the following:

root@ubuntu:/dev # ls -l /dev/parport0
crw-rw----  1 root lp 99, 0 2005-05-09 09:10 /dev/parport0

so the ownership is a little bit differently setup .... 

what i did to make it work is change the group ownership to scanner as ..
the user i set up is part of the group scanner

so i did ..

root@ubuntu:/dev # chown root:scanner parport0
root@ubuntu:/dev # ls -l /dev/parport0
crw-rw----  1 root scanner 99, 0 2005-05-09 09:10 /dev/parport0

as you can see the group ownership is scanner now ..

now run xsane from the menu ( normal user execution is working :) )

Xsane is starting up successfully

For all of you who have the same problem enjoy ....

try this .... it worked for me ...

Greetings,

Jellus

---

