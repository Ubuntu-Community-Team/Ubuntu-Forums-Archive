---
title: "ubuntu upgraded, acroread is broken."
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by kutlu on 2007-05-12
I previously made my acroread (Adobe reader 7.0) work in Ubuntu edgy. after I upgraded my ubuntu to 7.0 , acroread no more work.

not having acroread is not a problem, but my firefox is trying to open adobe files with acroread, and cannot open,gives error. I have to right click, download each time in order to see it.
It says
"could not launch Adobe Reader 7.0. please make sure it existsin Path variable in environment. If the problem persists, please reinstall the program"

I tried to reinstall but I opened synaptic to remove. It seemed that it is not installed. I tried to install, it gave error. the error is:


"Package acroread has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list"

acroread is not important at all, but I want to open when I click in firefox.

---

### Post by mozillar on 2007-05-12
Hi,

this may help resolve your issue. If I understand your question, you want to open pdf's in Firefox, but not have the browser point to the broken acroread plugin anymore.

In Firefox,  select Preferences from the Edit menu. On the Content tab, click on the Manage button to configure how Firefox handles certain types of files. If Acroread shows up in this list, I would try to Remove Action. Then try to open a pdf in Firefox and select Document Viewer or Evince as the default handler for pdf files.

If this fixes your issue, you may want to finish by cleaning up the Firefox plugins. Type "about:plugins" as the URL and see if the acroread plugin is still being loaded. If it is, search for the plugin filename. One way to search for this plugin is to type " find /. -name "xxx.so" in a terminal (replace xxx with the plugin filename). Once found, simply delete the plugin file. It may exist in a couple locations, including ./usr/lib/firefox/plugins/

Good luck!!
-Ted

---

### Post by kutlu on 2007-05-14
> **mozillar said:**
> Hi,

this may help resolve your issue. If I understand your question, you want to open pdf's in Firefox, but not have the browser point to the broken acroread plugin anymore.

In Firefox,  select Preferences from the Edit menu. On the Content tab, click on the Manage button to configure how Firefox handles certain types of files. If Acroread shows up in this list, I would try to Remove Action. Then try to open a pdf in Firefox and select Document Viewer or Evince as the default handler for pdf files.

If this fixes your issue, you may want to finish by cleaning up the Firefox plugins. Type "about:plugins" as the URL and see if the acroread plugin is still being loaded. If it is, search for the plugin filename. One way to search for this plugin is to type " find /. -name "xxx.so" in a terminal (replace xxx with the plugin filename). Once found, simply delete the plugin file. It may exist in a couple locations, including ./usr/lib/firefox/plugins/

Good luck!!
-Ted

acroread is not shown in firefox's list of file association. and when I try to erase plugin file, it starts to warn me that I should install add-on in order to see the page.

it did not solve problem.

---

### Post by mozillar on 2007-05-14
Could you please post a screenshot of the dialog  showing "install add-on in order to see the page".  That sounds different than the std firefox dialog for selecting the helper app. 
Also, how did you delete the plugin file? In terminal, etc.

We should still be able to fix this.

---

### Post by kutlu on 2007-05-17
> **mozillar said:**
> Could you please post a screenshot of the dialog  showing "install add-on in order to see the page".  That sounds different than the std firefox dialog for selecting the helper app. 
Also, how did you delete the plugin file? In terminal, etc.

We should still be able to fix this.

it is classical warning which tries to install add on itself after clicking to "next", but it cannot and it directs to website of adobe so that you can download plugin.
so, it asks for the addon I've deleted.

I actually deleted it by terminal, I could not see any uninstallation procedure for this addon.

---

