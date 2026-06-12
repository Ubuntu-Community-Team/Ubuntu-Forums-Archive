---
title: "Libusb and how to its package"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by sh4rif on 2013-02-23
Hello everyone

I have a very important question... 
I have installed libusb by using the following command i am not sure if it was right or not and the command was 

[COLOR=SeaGreen]**sudo apt-get install libusb-dev**[/COLOR]

once I have installed (and I am not sure if it has installed or not), I want to know how would I use the library because I write some sample code which uses [SIZE=3]**<libusb.h >**[/SIZE] but when i compile that c++ file using "g++ test_libusb.cpp" that throws the following error, 
[COLOR=Red]
[SIZE=3]"test_libusb.cpp:2:20: fatal error: libusb.h: No such file or directory
compilation terminated."[/SIZE][/COLOR][SIZE=3]
[/SIZE]
I am clueless what to do cant find any source on the internet to get to the bottom of this... can anyone please help I am a desperate.. and please treat me as novice on both c/c++ and Ubuntu...

thanks a lot for you time folks

hoping for an early response... 

thanks one more time
Sharif

---

### Post by sh4rif on 2013-02-23
code for my cpp file is below

```
#include <iostream>
#include <libusb.h>

using namespace std;

int main(){
    //pointer to pointer of device used to retrieve a list of devices
    libusb_device **devs;
    libusb_device_handle *dev_handle; //a device handle
    libusb_context *ctx = NULL; //A LIBUSB session
    int r;// for return values
    ssize_t cnt; //holding number of devices in list
    r = libusb_init(&ctx); // initialize the library for the session we just declared
    
    if(r < 0){
        cout <<"init error "<<r<< endl;
        return 1;
    }
    
    libusb_set_debug(ctx, 3); // set verbosity level to 3, as suggested in the documentation
    cnt = libusb_get_device_list(ctx, &devs); //get the list of devices
    
    if (cnt < 0) {
        cout <<"Get Device Error "<< endl; // there was an error
        return 1;
    }
    
    cout <<cnt<<" Device in list "<< endl;
    dev_handle = libusb_open_device_with_vid_pid(ctx, 5118, 7424) // these are vendor id and product id
    
    if (dev_handle == null){
        cout<<"Cannot open device "<<endl;
    }else{
        cout<<"Device opened"<<endl;
    }
    
    libusb_free_device_list(devs, 1);// free the list unref the devices in it
    
    unsigned char *data = new unsigned char[4];//data to write
    data[0] = 'a';data[1] = 'b';data[2] = 'c';data[3] = 'd';//some dummy values
    
    int actual; //used to find how many bytes were written
    
    if (libusb_kernal_driver_active(dev_handle, 0) == 1){// findout if kernal driver attached
        cout<<"Kernal Driver Active"<<endl;
        if(libus_detach_kernal_driver(dev_handle, 0) == 0 ){    //detach it
            cout<<"Kernal Driver Detached"<<endl;
        }
    }
    
    r = libusb_claim_interface(dev_handle, 0);// claim interface 0 (the first) of devices
    
    if(r < 0){
        cout <<"Cannot claim interface "<<endl;
        return 1;
    }
    
    cout <<"Claimed interface "<<endl;
    
    cout<<"data->"<<data<<"<-"<<endl; // just to see the data we want to write : abcd
    cout<<"Writing data..."<<endl;
    
    r = libusb_bulk_transfer(dev_handle, (2 | LIBUSB_ENDPOINT_OUT), data, 4, &actual, 0);//my device's out endpoint was 2, found withe trial - the device had two endpoints: 2 and 129
    
    if(r == 0 && actual == 4){    // we wrote 4 bytes successfully
        cout<<"Writing successfull"<<endl;
    }else{
        cout<<"write error"<<endl;
    }
    
    r = libusb_release_interface(dev_handle, 0); // release the claimed interface
    
    if (r != 0){
        cout<<"Cannot release interface"<<endl;
        retrun 1;
    }
    cout<<"Released interface"<<endl;
    libusb_close(dev_handle); // close the device we opened
    libusb_exit(ctx); // need to be called to end the
    
    delete[] data// delete the allocated memory for data
    return 0;
    //printf("Hello libusb!");
    //return 0;
}
```

---

### Post by steeldriver on 2013-02-23
I think the header file supplied by that package is called usb.h (not *lib*usb.h) - try changing your include instruction to

```
#include <usb.h>
```

---

### Post by sh4rif on 2013-02-23
this does not work coz if you check other examples (btw i have copied this example from a website) they are all using libusb

---

### Post by steeldriver on 2013-02-23
Well that file is not part of the libusb-dev package (at least, not on 12.04)

```
$ apt-file show libusb-dev | grep '\.h$'
libusb-dev: /usr/include/usb.h

```It seems to be in **libusb-1.0-0-dev**

```
$ apt-file search -x 'libusb\.h$'
apcupsd-doc: /usr/share/doc/apcupsd/examples/libusb.h
**libusb-1.0-0-dev: /usr/include/libusb-1.0/libusb.h**

```Note that because it's in a subdir of /usr/include you would need to specify it as

```
#include <libusb-1.0/libusb.h>
```or add a -I include path

If you want to search on your own system, you can use the apt-cache tool and/ or install apt-file - it's very useful for tracking down this kind of thing

---

### Post by sh4rif on 2013-02-23
thank you very much "[[COLOR=#000000]steeldriver[/COLOR]]("http://ubuntuforums.org/member.php?u=1627500")" that explanation clears some confusion in my mind but...thanks once again for that

btw which one is the latest and which one should i use?
**libusb-dev** or **libusb-1.0-0-dev **(considering I am a layman in c/c++ and libusb)
any resources to learn or understand libusb just wanna run a simple code... 

thanks once again you are a STAR 10 out of 10 for your effort

---

