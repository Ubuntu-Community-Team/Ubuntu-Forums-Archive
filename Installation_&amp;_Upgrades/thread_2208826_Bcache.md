---
title: "Bcache"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by epicfeil on 2014-03-02
Hello everyone, i have an asus ux32vd running linux mint petra (based on ubuntu 13.10).
 This model has a mechanical HDD and a soldered 24gb ssd used as cache with intel srt (on windows). I know bcache can do the same job and its included in the 3.10+ kernels so i decided to go for it! I ve read the installation and configuration of bcache but since im almost a beginnner i cant get out of it, also there is near 0 community documentation about it... I ask for some help if its easy to set up and its just me that cannot understand the configuration, otherwise i ask if someone knows about general gnu linux or debian based guides that can help me to better understand linux in general and hoping this will help me to set up bcache on my own, and perhaps share my knowledge about it.

---

### Post by grahammechanical on 2014-03-02
If I understand this tutorial, and anyone can correct me if I am wrong, this is what is needed

1) A SSD with a Linux operating system on it.
2) A SSD to be the cache
3) A hard disk

[https://www.linux.com/learn/tutorials/754674-using-bcache-to-soup-up-your-sata-drives](https://www.linux.com/learn/tutorials/754674-using-bcache-to-soup-up-your-sata-drives)

The tutorial does not mention sda, which I presume is the SSD holding the Linux operating system. It seems a very simple thing to do. That also means that is very simple to break the OS.

Regards.

---

### Post by epicfeil on 2014-03-03
Oh ok so i have to do this from an already running system!  I could also try from a live cd i presume!  Thx i didnt get it at first, i read about a maintboot method to change an existing system filesystem from ext4 to bcache, ill try to post it here when i am back home!  I do apologise for my english, it may be real bad, it s not my first lang

---

### Post by epicfeil on 2014-03-19
Hello, i saw there is a maintboot method that allows conversion to bcache fs from an existing installation. Whats unclear to me its if i have to still do it from an "external running system". Anyway i probably misunderstood the instructions but here is what i did : (sdb1 = cache , sda2 = \ , and i am running ubuntu 13.10 64 bit now)

installed bcache and everything needed.
created cache with: sudo make-bcache -C /dev/sdb1
now there is the part where i should add my root to the new bcache filesys and since i am on a running system the command should be this one:
sudo blocks to-bcache --maintboot /dev/sda2 --join bcache UUID

and i have an errror..... this is the output :

sasso@sasso-UX32VD:~$ sudo blocks to-bcache --maintboot /dev/sda2 --join e0f5a832-6cf8-4ed9-8acd-dc454b3b6ca4

Get: 1 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/main cdebconf amd64 0.182ubuntu1 [163 kB]
Get: 2 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/universe febootstrap all 4.1.1-3 [1766 B]
Get: 3 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/main gawk amd64 1:4.0.1+dfsg-2.1ubuntu2 [781 kB]
Get: 4 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/main libdebian-installer4 amd64 0.87ubuntu4 [25,8 kB]
Get: 5 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/main libsigsegv2 amd64 2.10-2 [15,0 kB]
Get: 6 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/main libtextwrap1 amd64 0.1-14 [10,1 kB]
Get: 7 [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) saucy/universe original-awk amd64 2011-08-10-2 [74,5 kB]
Fetched 1071 kB in 1s (614 kB/s)      
Traceback (most recent call last):
  File "/usr/bin/maintboot", line 86, in <module>
    script_main()
  File "/usr/bin/maintboot", line 82, in script_main
    sys.exit(main())
  File "/usr/bin/maintboot", line 69, in main
    + ['--initrd', tdir + '/initramfs', tdir + '/kernel'])
  File "/usr/lib/python3.3/subprocess.py", line 542, in check_call
    retcode = call(*popenargs, **kwargs)
  File "/usr/lib/python3.3/subprocess.py", line 523, in call
    with Popen(*popenargs, **kwargs) as p:
  File "/usr/lib/python3.3/subprocess.py", line 824, in __init__
    restore_signals, start_new_session)
  File "/usr/lib/python3.3/subprocess.py", line 1448, in _execute_child
    raise child_exception_type(errno_num, err_msg)
FileNotFoundError: [Errno 2] No such file or directory: 'kexec'
Traceback (most recent call last):
  File "/usr/bin/blocks", line 9, in <module>
    load_entry_point('blocks==0.1.4', 'console_scripts', 'blocks')()
  File "/usr/lib/python3/dist-packages/blocks/__main__.py", line 2002, in script_main
    sys.exit(main())
  File "/usr/lib/python3/dist-packages/blocks/__main__.py", line 1668, in main
    return args.action(args)
  File "/usr/lib/python3/dist-packages/blocks/__main__.py", line 1748, in cmd_to_bcache
    device, 'to-bcache', debug=args.debug, join=args.join)
  File "/usr/lib/python3/dist-packages/blocks/__main__.py", line 1770, in call_maintboot
    + ['--append', 'BLOCKS_ARGS=' + encoded])
  File "/usr/lib/python3.3/subprocess.py", line 547, in check_call
    raise CalledProcessError(retcode, cmd)
subprocess.CalledProcessError: Command '['maintboot', '--pkgs', 'python3-blocks', 'util-linux', 'dash', 'mount', 'base-files', 'libc-bin', 'nilfs-tools', 'reiserfsprogs', 'xfsprogs', 'e2fsprogs', 'btrfs-tools', 'lvm2', 'cryptsetup-bin', 'bcache-tools', '--initscript', '/usr/lib/python3/dist-packages/blocks/maintboot.init', '--append', 'BLOCKS_ARGS=%7B%22debug%22%3A%20false%2C%20%22join%22%3A%20%22e0f5a832-6cf8-4ed9-8acd-dc454b3b6ca4%22%2C%20%22command%22%3A%20%22to-bcache%22%2C%20%22device%22%3A%20%2232769750-d3c7-4a87-82a7-05351eabb26e%22%7D']' returned non-zero exit status 1


what should i do now? im kinda stuck, should i post on github for solution? thx

---

### Post by epicfeil on 2014-03-22
bump !

---

