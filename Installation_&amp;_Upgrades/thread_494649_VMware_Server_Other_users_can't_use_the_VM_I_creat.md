---
title: "VMware Server: Other users can't use the VM I created"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by BYOCOM on 2007-07-07
I created a Windows XP VM to run some Windows-only stuff.  I can use it fine and everything works great for me but when I log in as another user, I can't use the VM.

Logged in as the other user, I can launch the VMware Server console but there is nothing in the inventory.  If I right-click in the inventory area and select "Open..." and browse to the .VMX file I get an error that says 'Unable to add virtual machine "/var/lib/vmware-server/Virtual Machines/Windows XP Pro/Windows XP Pro.vmx" to the inventory: No permission to perform this operation'

The error sounded like a permissions issue to me.

I tried creating a group called "vm-users", changed the group to "vm-users" on each of the files in the "Windows XP Pro" folder that contains the .VMX file as well as the folder itself, and gave the "vm-users" group rwx permissions to each file and the containing folder as well but still no dice.

I'm not completely new to Linux and Ubuntu but I'm not a seasoned pro either.

Any ideas?

---

### Post by BYOCOM on 2007-07-07
Aggghh.  Ok scratch this.  PEBKAC.

I had the VM set to "Make this virtual machine private".  I just unchecked that within the VM settings and everything works great for the other user.  I must have done that when I created it.

So in case anyone was wondering if that feature works, it does :)

---

### Post by cover3 on 2007-08-27
man, this simple fix saved me a lot of research time.  thx for the tip!

---

### Post by breel77 on 2007-09-05
Apparently I created my vm as root and had the same situation.

Not really sure how i managed to do that unless i was a *genius* and started it up w/ sudo

Anyway to solve my situation i had to run:

sudo vmware-server-console 
and uncheck private

---

