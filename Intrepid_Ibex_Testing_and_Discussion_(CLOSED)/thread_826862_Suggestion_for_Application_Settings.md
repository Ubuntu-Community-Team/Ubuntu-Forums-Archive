---
title: "Suggestion for Application Settings"
date: 2008-06-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jfbilodeau on 2008-06-12
Good day all,

If it hasn't been proposed already, I would like to suggest that we use a new environment variable that would determine where application settings should be stored.

Right now, all settings are stored in the user's home folder, under hidden directories. The problem I find is that it makes the home directory very messy. I know I can choose to show or hide 'hidden' files, but I usually keep my hidden files visible. Furthermore, being a bit of a distrowhore, I like to install different distros while reusing the same home directory.

I know it's not feasible to rewrite every single application to use a new environment variable to determine where to store settings for the Intrepid, but this is something we can slowly work towards.

To get the ball rolling, I would like to suggest something like:
USER_SETTINGS="~/.settings"
or
USER_SETTINGS="~/Settings"
or
USER_SETTINGS="~/.ubuntu_settings"

During transition, an application may need to look for it's setting in either $HOME or $USER_SETTING. From this point forward, an application would save it's settings under $USER_SETTINGS. If $USER_SETTINGS does not exists, then $HOME would be used.

Again, I know that this is not a trivial change to the way most Linux applications are written, but I believe that it will further improve the design of our beloved OS.

What do you think?

J-F

---

### Post by diafanos on 2008-06-12
+1

---

### Post by xebian on 2008-06-12
> **jfbilodeau said:**
> Good day all,

If it hasn't been proposed already, I would like to suggest that we use a new environment variable that would determine where application settings should be stored.

Right now, all settings are stored in the user's home folder, under hidden directories. The problem I find is that it makes the home directory very messy. I know I can choose to show or hide 'hidden' files, but I usually keep my hidden files visible. Furthermore, being a bit of a distrowhore, I like to install different distros while reusing the same home directory.

I know it's not feasible to rewrite every single application to use a new environment variable to determine where to store settings for the Intrepid, but this is something we can slowly work towards.

To get the ball rolling, I would like to suggest something like:
USER_SETTINGS="~/.settings"
or
USER_SETTINGS="~/Settings"
or
USER_SETTINGS="~/.ubuntu_settings"

During transition, an application may need to look for it's setting in either $HOME or $USER_SETTING. From this point forward, an application would save it's settings under $USER_SETTINGS. If $USER_SETTINGS does not exists, then $HOME would be used.

Again, I know that this is not a trivial change to the way most Linux applications are written, but I believe that it will further improve the design of our beloved OS.

What do you think?

J-F
Nice try but try looking at LSB standards.  I believe Ubuntu is now compliant?

---

### Post by jfbilodeau on 2008-06-12
> **xebian said:**
> Nice try but try looking at LSB standards.  I believe Ubuntu is now compliant?
I've looked quickly, and I can't find anything about application configuration files.

However, I'm not sure that this would break LSB. The 'classic' approach to saving settings continues to works. However, should an application choose to support the extension, it can.

Right now, following LSB, it means that practically everytime I install a new distribution, I have to wipe out my Gnome or KDE settings because there's enough variation that the desktop is totally skewed. Themes and menu organization are examples of configuration that is not portable from one distro to the next.

It would be really nice to be able to have control over the location of my settings.

---

### Post by MaX on 2008-06-12
There already is a specification for it....

Read this thread [Should we file bugs against apps not following XDG specification?]("http://ubuntuforums.org/showthread.php?t=801987")

---

### Post by Eclipse. on 2008-06-12
- 1
 
This would need to be done upstream with collaboration from alot of projects.
 
The way things are just now with .program_name/ is fine.Using .local and .config ect just messes things up when you have multiple os's using /home.

Instead of moaning about it seeing them why dont you just hide them like they are by default.

---

### Post by jfbilodeau on 2008-06-12
> **MaX said:**
> There already is a specification for it....

Read this thread [Should we file bugs against apps not following XDG specification?]("http://ubuntuforums.org/showthread.php?t=801987")

Thanks for the link. I checked it out, and that's pretty much what I was hoping to see. From the sounds of it, it's still a work in progress, but I think it's progress in the right direction.

---

### Post by psyke83 on 2008-06-12
> **jfbilodeau said:**
> Themes and menu organization are examples of configuration that is not portable from one distro to the next.

Yes, but that has nothing to do with user settings. Themes are rarely stored per user (due to theming difficulties for root/priviledged applications), and menu organization is defined by distribution packaging. Your proposal will not make this any easier or different.

---

### Post by jfbilodeau on 2008-06-12
> **Eclipse. said:**
> 
The way things are just now with .program_name/ is fine.Using .local and .config ect just messes things up when you have multiple os's using /home.

Instead of moaning about it seeing them why dont you just hide them like they are by default.

Thanks for you candid reply. However, I don't think that just using .program_name is fine as-is. It removes control over my home directory, and creates a mess of hidden directory. Why should the application setting directories be intermixed with my documents, desktop, etc?

Control over .local and .config (as in an envvar) would actually make it easier to share my home between distros.

Sure, I can hide and show hidden files with the touch of a key, but this is not what I'm 'moaning' about. I'm saying that I would prefer to have a clean home directory that I can control. It seems that the XDG specification found [here]("http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html") is already ahead of what I'm proposing.

---

### Post by jfbilodeau on 2008-06-12
> **psyke83 said:**
> Yes, but that has nothing to do with user settings. Themes are rarely stored per user (due to theming difficulties for root/priviledged applications), and menu organization is defined by distribution packaging. Your proposal will not make this any easier or different.

I agree that the themes are protected, but the *selected* theme is a user setting. When I install Ubuntu, it defaults to the Human theme. However, when I install Fedora or OpenSUSE, they will be unable to find the Human theme, thus giving be a very ugly looking desktop.

Selecting a new theme in that distro means that when I reboot in Ubuntu, I may find myself in the same boat, since the chosen theme may not be installed.

Themes are just the tip of the iceberg. Menus have been a problem for me (ie: Cedega) and default desktop configuration (ie: panels, gadget, etc) amongst other things.

Being able to choose where the configuration for my application goes would mean that I could boot between my distros, and not have to cripple/reset my desktop layout.

---

### Post by Eclipse. on 2008-06-12
> **jfbilodeau said:**
> Thanks for you candid reply. However, I don't think that just using .program_name is fine as-is. It removes control over my home directory, and creates a mess of hidden directory. Why should the application setting directories be intermixed with my documents, desktop, etc?

Control over .local and .config (as in an envvar) would actually make it easier to share my home between distros.

Sure, I can hide and show hidden files with the touch of a key, but this is not what I'm 'moaning' about. I'm saying that I would prefer to have a clean home directory that I can control. It seems that the XDG specification found [here]("http://standards.freedesktop.org/basedir-spec/basedir-spec-0.6.html") is already ahead of what I'm proposing.

Sorry, moaning wasn't really the right word.

The home directory is "clean" with hidden files disabled, you really should have them unhidden only if your looking to do something pacifically with a programs settings.Also I don't understand what problems you have been having with it removing control of your home directory I have never had any problems like that.

For this to be done it would need to be done at a higher level and would require alot of work for which in my opinion doesn't really give much back.

---

### Post by jfbilodeau on 2008-06-12
> **Eclipse. said:**
> Sorry, moaning wasn't really the right word.

The home directory is "clean" with hidden files disabled, you really should have them unhidden only if your looking to do something pacifically with a programs settings.Also I don't understand what problems you have been having with it removing control of your home directory I have never had any problems like that.

For this to be done it would need to be done at a higher level and would require alot of work for which in my opinion doesn't really give much back.

Thanks again for the reply. I think it's fair to say that the home directory 'looks' clean with the hidden files disable, but I'm often working with hidden files on for the simple fact that I'm a tinkerer and I like mucking around my system. However, that's not the root of my gripe ;)

My two issues are that I feel that the root of the home directory should not be used to store application configurations. Instead, a sub-directory should be used. The other, and probably more important issue is that I would like to be able to keep the same home directory across different distros, but not the settings. In other words, I would like to have access to Documents, Desktop, Music and whatever else, but I would like to be able to avoid configuration clash between Ubuntu and other distro.

I understand that it's impossible for Ubuntu to rewrite every application to use a new settings directory. What I'm proposing is that we offer a mechanism that allows the application developer to find out which directory should be used to save settings. It seems that this initiative is already underway with freedesktop.org, thus making my suggestion redundant.

I agree that it will be a lot of work for developers (myself included) to migrate their code to the proposed standard, but I think that there is a lot to give back, including the ability to back/transfer just your desktop settings, amongst others.

Hope that clarifies what I'm saying! :)

---

