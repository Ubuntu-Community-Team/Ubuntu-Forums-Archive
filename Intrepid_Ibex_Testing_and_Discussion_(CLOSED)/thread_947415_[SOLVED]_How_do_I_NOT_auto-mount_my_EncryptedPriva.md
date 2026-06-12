---
title: "[SOLVED] How do I NOT auto-mount my EncryptedPrivateDirectory at startup?"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by willz06jw on 2008-10-14
Howdy,

I am using the new 8.10 Intrepid Beta and I have installed the EncryptedPrivateDirectory. (By the way cheers on the great work I give you )

Every time I start my computer the Private folder is mounted automatically. I want to use this folder to store sensitive information and I also like having Ubuntu auto-login. 

Is there a way to have it mount only when I want and have it request a password?

Thanks,
Will

---

### Post by taavikko on 2008-10-14
> **willz06jw said:**
> Howdy,

I am using the new 8.10 Intrepid Beta and I have installed the EncryptedPrivateDirectory. (By the way cheers on the great work I give you )

Every time I start my computer the Private folder is mounted automatically. I want to use this folder to store sensitive information and I also like having Ubuntu auto-login. 

Is there a way to have it mount only when I want and have it request a password?

Thanks,
Will

remove the automount script in .ecryptfs/

---

### Post by nystire on 2008-10-14
Is there no way to do this from the GUI?

---

### Post by taavikko on 2008-10-14
> **nystire said:**
> Is there no way to do this from the GUI?

Open nautilus, show hidden folders, and then remove the contents from .ecryptfs/
automount & autoumount

nothing else!

---

### Post by NoFearDJB on 2008-10-14
> **taavikko said:**
> remove the automount script in .ecryptfs/

Thank you, I'll give this a try later, I've been wondering the same thing!

---

