---
title: "Using Eucalyptus (Ubuntu 9.04 [Jaunty])"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by poszest16 on 2009-04-12
OK, So I installed the Beta Release of Ubuntu 9.04 [Jaunty] [Server] the other day. Everything works great except using ATI X300 Graphic Drivers. But that is a different subject.

My question for this thread is how do you properly use Eucalyptus under Jaunty? I installed all the required packages using apt-get and Eucalyptus seems to be functioning correctly. The only available guide I could find for using Eucalyptus is at "http://eucalyptus.cs.ucsb.edu/wiki/EucalyptusAdministratorGuide_v1.4". So far the guide is working OK. But there is a few problems I'm having.

1st: Eucalyptus is not starting at startup (I'm telling it to but is not.)

2nd: Starting the Eucalyptus gives warnings but is functional.
```

root@server:~# /etc/init.d/eucalyptus-cc start
 * Starting Eucalyptus Cluster Controller eucalyptus                                                                     (98)Address already in use: make_sock: could not bind to address 0.0.0.0:8774
no listening sockets available, shutting down
Unable to open logs
Failed to start the CC!

```

```

root@server:~# /etc/init.d/eucalyptus-nc start
 * Starting Eucalyptus Node Controller eucalyptus                                                                        Warning! Cannot find bridge xenbr0: instances may be without net
(98)Address already in use: make_sock: could not bind to address 0.0.0.0:8775
no listening sockets available, shutting down
Unable to open logs
Failed to start the NC!

```

```

root@server:~# /etc/init.d/eucalyptus-cloud start
 * Starting Eucalyptus Cloud Controller eucalyptus                                                                [ OK ] 

```

3rd: The biggest problem I am having is building AMI's. First I had a hard time to locate where to download "euca-ttylinux.tgz" from. After much searching I downloaded it and continued the guide.

```

root@server:/usr/share/eucalyptus# ec2-bundle-image -i ttylinux/vmlinuz-2.6.16.33-xen --kernel true
Please specify a value for arch [i386]: 
Bundling image file...
Splitting /tmp/vmlinuz-2.6.16.33-xen.tar.gz.enc...
Created vmlinuz-2.6.16.33-xen.part.0
Generating digests for each part...
Digests generated.
Creating bundle manifest...
ec2-bundle-image complete.

# The following gives to same error no matter what.
root@server:/usr/share/eucalyptus# ec2-upload-bundle -b kernel-bucket -m /tmp/vmlinuz-2.6.16.33-xen.manifest.xml
invalid option: --ec2cert
Try 'ec2-upload-bundle --help'

# After the following command I receive a message that "ec2-init" has crashed.
root@server:/usr/share/eucalyptus# ec2-register kernel-bucket/vmlinuz-2.6.16.33-xen.manifest.xml
Server: Binding 'ec2_amazonaws_com_doc_2009_03_01' not found for class edu.ucsb.eucalyptus.msgs.RunInstancesType

```

If anyone can help or suggest steps to get my private cloud server up and running would be greatly appreciated.

---

### Post by nurmi on 2009-04-12
Greetings,

We've just posted some detailed 'getting started with Eucalyptus on Ubuntu' documentation over at:

[https://help.ubuntu.com/community/Eucalyptus](https://help.ubuntu.com/community/Eucalyptus)

There, it walks through first time configuration and creating an image using vmbuilder for use in Eucalyptus.  Part of your specific problem is addressed there as well, which is that Eucalyptus supports a slightly older version of the EC2 AMI tools since they dropped the ec2cert option in later versions.  

Hope the new documentation helps!

---

### Post by poszest16 on 2009-04-13
Thanks for your reply that guide seems to be working great. I am only now having one problem so far. When creating the Kernel and I execute command
```
ec2-upload-bundle -b kernel -m ./kernel/vmlinuz-2.6.28-11-generic.manifest.xml

```
The command says missing argument --access-key and --secret-key. I assume the access key and secret key are the ones listed on at [https://localhost:8443](https://localhost:8443). Which must be incorrect because executing the command with these arguments it returns.
```
user@server:/ubuntu-kvm$ /usr/share/ec2-ami-tools-1.3-26357/bin/ec2-upload-bundle -b kernel -m ./kernel/vmlinuz-2.6.28-11-server.manifest.xml --access-key <access key> --secret-key <secret key>
Server.InvalidAccessKeyId(403): The AWS Access Key Id you provided does not exist in our records.
Bundle upload failed.

```
I am sure this error would happen even if I was uploading the ramdisk and/or image.

**UPDATE:**

After some testing I found my ec2 files where under the wrong directories. But now I'm getting the error under some commands
```
user@server:/ubuntu-kvm$ EMI=`ec2-register image/root.img.manifest.xml | awk '{print $2}'`
Server: WS-Security screw up -- unauthorized user has authorized certificate: admin-090412232559

```

I don't know if this would help but I get this when restarting RC2-INIT
```
root@server:~$ /etc/init.d/ec2-init restart
 * Setting EC2 defaults                                                                                                                                                   [fail] 
 * Fetching EC2 login credentials                                                                                                                                         [fail] 
 * Running EC2 user data                                                                                                                                                  [ OK ] 
 * Setting hostname to EC2 public_hostname                                                                                                                                [fail] 
 * Determining EC2 availability zone                                                                                                                                             !!! Unable to connect to 169.254.169.254.
                                                                                                                                                                          [ OK ]

```

---

### Post by nurmi on 2009-04-16
Greetings,

When you download your Eucalyptus credentials, it should drop a file called 'eucarc' that you'll need to source before running the tools.  I suspect that is what is going on with those error messages. Is that possible?

Regards

---

