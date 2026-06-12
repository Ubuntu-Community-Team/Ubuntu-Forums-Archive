---
title: "Newbie installation of Ubuntu"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by sunrise718 on 2018-07-18
I am going to install Ubuntu on a Dell laptop with an expired version of Ubutuntu that was purchased with Ubuntu preloaded.  

I want to wipe out the existing installation and start fresh by selecting the full installation mode (not dealing with partitions).  

The installation should walk me through the process and include the ext4 partition automatically for me, right?  Nothing "extra" is required for the ext4 partition if I want to use the entire drive for the installation?

Also, if I purchase a laptop with Windows and erase Windows, the installation will completely erase Windows and replace it with the ext4 partition and override Windows NTFS.  Right?  

The same should be true for installing Mint, etc.  

Thanks in advance. ;)

---

### Post by Autodave on 2018-07-18
Installing Ubuntu (or most derivatives) over top of an existing Ubuntu is easy: insert your boot medium and choose to replace whatever Ubuntu is already on there.

Replacing Windows will require you to at least turn off *fast boot *in the BIOS so that Windows releases control of the hard drive. From there, it will be pretty much the same. You will have to decide if you want UEFI or legacy boot. With your install medium, choose to *erase Windows and use entire disk.*

Either scenario, make sure that you have backed up anything that you wish to keep.

---

### Post by TheFu on 2018-07-18
Yes.  But doing an install isn't something you should do once.  Practice for anything makes us better at it.  Do it 5 times picking  different installation options and see what results. After all, you are already wiping the system, so there isn't anything to be lost.

BTW, having 1 partition isn't a "best practice" for desktop Linux installations.  There are lots of questions here about setting up partitions, each full of good advice.

Whenever I setup a new desktop, I want to  use LVM and 4 LVs (these are logical volumes, sorta like a partition, but 10x more flexible).  There is an option during installation to "Use LVM". I'd recommend that as a choice for anyone on a physical machine. As your skills grow, you'll find things that LVM provides which other options don't allow.  The main thing with choosing LVM is to not allow old kernels to stay around.  Keeping 2-3 old kernels around is good, but more than that can cause /boot/ to fill up and lead to bad problems during patching.

Also, I always use full disk encryption, FDE, with laptops for a number of reasons.  There's a checkbox for that in the installer. It will use both encryption AND LVM.

Welcome to the forums.

---

### Post by sunrise718 on 2018-07-18
Thank you for responding.  Holy crap, though, it took me a long time to log in to reply.  This forum is way too complicated and confusing.  It is hard to see how to login.  You need a manual just for that alone.  It should be more straightforward.  

That said, the response time on here is wonderful and appreciated.  I just wish I had an easier time logging in to reply.  I will probably struggle again the next time.  

My other question is with setting up a password during installation.

I believe that the initial installation password is the superuser password.  Then, after that, each user creates their own desktop.  Is that right?  

If that is correct, is the superuser password ever needed for anything other than installation?

---

### Post by sunrise718 on 2018-07-18
When you say "physical machine," I think you are referring to a desktop and not a laptop PC.  Right?  I'm using laptops so I'm not sure if I need the LVM but might consider it.  However, as a newbie, it seems easier to start with a whole-disk installation.  So, if only have one partition, it's difficult to clean up the old kernels.  The kernels are left over when installing updates?

---

### Post by TheFu on 2018-07-18
> **sunrise718 said:**
> I believe that the initial installation password is the superuser password.  Then, after that, each user creates their own desktop.  Is that right?  

If that is correct, is the superuser password ever needed for anything other than installation?

No. Ubuntu doesn't have a root password.  There are regular userids and some can be in the sudo/admin groups, if you like.  You can add new accounts and make then part of those groups, if you like, then remove the first userid created during installation.

But never leave your system without at least 1 userid in the sudo and adm groups, unless you want to be forced to hack back in or reinstall.

Access to root account on Ubuntu is frowned on.

On other Linux distros, access to root is provided at install time. Ubuntu thinks this is a poor security choice. I agree.

---

### Post by TheFu on 2018-07-18
> **sunrise718 said:**
> When you say "physical machine," I think you are referring to a desktop and not a laptop PC.  Right?  I'm using laptops so I'm not sure if I need the LVM but might consider it.  However, as a newbie, it seems easier to start with a whole-disk installation.  So, if only have one partition, it's difficult to clean up the old kernels.  The kernels are left over when installing updates?

No. Physical machine is different from a virtual machine. Laptops and desktops are both physical machines.  Whether you use LVM or not is a choice. Whether you use FDE or not is a choice.

If you practice the install a few times, you'll see these options.  They aren't hidden.

Cleaning old kernels is part of the 'apt' script. I don't use GUI tools for patching, so don't know how those work. Sorry.
apt-get leaves old kernel.
aptitude leaves old kernels.
apt keeps 2-3 old kernels, but removes older ones.

This is for 16.04.  I haven't used 18.04 enough to know how each of those work on it.

---

