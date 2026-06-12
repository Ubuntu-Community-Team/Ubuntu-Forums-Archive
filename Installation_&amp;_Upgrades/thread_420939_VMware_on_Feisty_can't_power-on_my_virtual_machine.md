---
title: "VMware on Feisty: can't power-on my virtual machines"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by thoughts on 2007-04-24
I was running VMware server (from VMware-server-1.0.1-29996.tar.gz on the VMware website) on Edgy with no problems.  After upgrading to Feisty, of course I had to recompile VMware's kernel modules, but that was failing until I used the [any-to-any patch](http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0).

Now VMware is installed and I can run the "vmware" command to get my VMware Server Console.  But when I click on any of my Virtual Machines and hit the power-on button, I get this error:

> Unable to change virtual machine power state: The process exited with an error: End of error message.

And I then get an error-log at /tmp/vmware-username/NNNNN.log which contains this:

> Apr 24 02:23:39: vmx| [msg.vmmonPosix.badVersion] Version mismatch with vmmon module: expecting 138.0, got 137.0.
Apr 24 02:23:39: vmx| [msg.vmmonPosix.badDriver] You have an incorrect version of the `vmmon' kernel module.
Apr 24 02:23:39: vmx| Try reinstalling VMware Server.

I've uninstalled and reinstalled it multiple times now, both version 1.0.1 (which worked under Edgy) and the newer 1.0.2 (which I didn't try under Edgy).  But it always ends up this way, saying that I have the wrong vmmon module.

Any ideas?

Thanks,

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by thoughts on 2007-04-24
...and as usual, after spending the whole day searching in vain for a solution, I discover the solution immediately after posting my question to the forum :)

I found the solution [here](http://ubuntuforums.org/showpost.php?p=2509584); it is:

> 
(first extract the VMware server tarball)

cd vmware-server-distrib/lib/modules/source/
tar -xvf vmmon.tar
vim vmmon-only/include/compat_kernel.h

change the line that says:
     static inline _syscall1(int, compat_exit, int, exit_code);
to the following by removing two commas:
     static inline _syscall1(int compat_exit, int exit_code);

sudo tar -cvf vmmon.tar vmmon-only/

(then run vmware-install.pl as usual)


And the any-to-any patch is not needed now.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by SniperSlap on 2007-04-24
I tried your solution, and it still isn't working.  I'm still getting the same error.

This is really strange because I have vmware modules loaded........

Grr!

---

### Post by eentonig on 2007-04-24
Check if you have the same issue running the program as root. If this solves the issue, check the file permission on the VMWARE folder and files in your home directory.

I had the same issue because they were owned by root.

---

### Post by SniperSlap on 2007-04-24
Well!

That did 'er.

Here you go everybody, another part to the solution!

```
cd ~
sudo chown -R .vmware
```

---

