---
title: "User profile"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by Pan007 on 2005-08-01
](*,)  ](*,) 
I'm trying to create an user profile with restrictions. Can anyone please help me with this.

I want to create an profile for students, where there are restrictions and where the desktop can't be changed.

The user shall not be able to access terminal.
The user shall not be able to ''sudo''.
The user shall not be able to change the desktop. (He/she can change it, but when computer is restarted, the desktop is back to ''normal''.)
The user shall only be able to change his/her's own files

Is this possible?

Are there any easy way to do this?

Thanks in advance. :)

---

### Post by adwait on 2005-08-01
They students will not be able to use sudo anyway, because by default, the users created after the first one are not in the sudoers list. By default, a user can access only his files. As for not accessing the terminal......that could be difficult, no idea how that is done. Same for wallpapers.

---

### Post by Pan007 on 2005-08-01
Thanks for replying.

There must be a way for creating mandatory user profiles under linux?
This is a must when your're administrating a schools network. 

Please anyone with good solutions, help me with this.

I was able to access pictures under ''first user'' home directory, and use them as wallpapers as ''secondary user'' user. Is this right?

I tried to let ''secondary user'' use audio devices and video acceleration, but nothing else under System --> Administration --> User and Groups --> Properties.
Result: No sound, full access to CD-Rom device, user could not add printer......

''secondary user can access ''first user'' home directory?!

---

### Post by timothywcrane on 2006-07-08
If youare willing to give up your Gnome desktop for KDE (please no return flames) than you might check out the KDE kiosk tool [http://extragear.kde.org/apps/kiosktool/](http://extragear.kde.org/apps/kiosktool/) 

This should give you most of the control that you are looking for.


If all else fails, you can track down the configuration files and others that you may need to control, and set the permissions on them to allow reading and executing on them for your users, but make sure that the write function is disables for all except root. open shell #man chmod (I assume everybody already knows what little I know, but I like to see myself write) lol:D

---

### Post by scxtt on 2006-07-08
have you gone to System --> Administration --> Users & Groups then clicked on "properties" and "User Privileges"?

---

