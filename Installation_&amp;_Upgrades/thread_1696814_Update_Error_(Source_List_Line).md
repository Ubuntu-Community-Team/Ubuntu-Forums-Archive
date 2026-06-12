---
title: "Update Error (Source List Line)"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by ahmedm989 on 2011-02-27
After trying to install LibreOffice 3 using the directions on **[this]("http://www.mydailytechtips.com/2010/10/how-to-install-libreoffice-in-ubuntu.html")** page, I came across the following error:

'E:Malformed line 63 in source list /etc/apt/sources.list (dist)'

I also tried this afterwards: ">sudo apt-get install libreoffice3" (before getting the error message).

Any help would be greatly appreciated. Thanks in advance.

---

### Post by ahmedm989 on 2011-02-27
I actually removed that line, as well as line 62, which were concerning libreoffice3. The update has no error now, but I don't think it fully uninstalled libreoffice. How can I make sure?

---

### Post by zenwalker on 2011-02-27
You want to make sure if the libreoffice is being removed??

Then it shouldnt be available to you in any of the system menus. Nor the package manager should display it as installed, nor you should be able to launch the libreoffice command from a terminal.

Even *whereis libreoffice* command also should return you nothing.

---

### Post by ahmedm989 on 2011-02-27
> **zenwalker said:**
> You want to make sure if the libreoffice is being removed??

Then it shouldnt be available to you in any of the system menus. Nor the package manager should display it as installed, nor you should be able to launch the libreoffice command from a terminal.

Even *whereis libreoffice* command also should return you nothing.

It wasn't available anywhere after installation actually, which I forgot to mention. I tried searching for it as well, and it wasn't in the menus either. I found the folder which seems to be the appropriate size, so I think I'm going to delete it and hope no stray files cause problems in the future.

---

### Post by zenwalker on 2011-02-27
When you un-install these packages via standard methods, the package manager or its related command tools make sure they do remove the system files as well. But they do retain your custom folders in your home dir.

---

### Post by ahmedm989 on 2011-02-27
> **zenwalker said:**
> When you un-install these packages via standard methods, the package manager or its related command tools make sure they do remove the system files as well. But they do retain your custom folders in your home dir.

I don't know what you mean, lol. Are you considering deleting the folder manually to be a standard method?

---

### Post by ahmedm989 on 2011-02-27
It's in the "/opt/" folder and won't let me delete it actually.

---

