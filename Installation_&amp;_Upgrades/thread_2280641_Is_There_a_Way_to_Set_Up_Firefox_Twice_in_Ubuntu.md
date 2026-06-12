---
title: "Is There a Way to Set Up Firefox Twice in Ubuntu?"
date: 2015-06-01
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2015-06-01
I have multiple browsers installed (in addition to Firefox, I have Opera, Chrome, and Chromium).  I need to run two browsers at once, splitting screen space.

This works, but it has to be two separate browsers, not the same one twice, because with one browser (even if you add in a tab splitter), your fundamental problem is that you are just using one set of folders and files, and you have to share the same set of cookies and other data as a consequence.  You need to have each instance of the browser picked to work in a separate set of folders so that the files do not intermingle.

But the browsers themselves are internally programmed to use a specific set of named  folders and files, so just trying to clone the original install to a second place isn't going to work.  If you made it a second drive, it would have its own separate folders and files, but it would default to sharing the ones used by the original install.  No gain there.  If you rebooted to a software install on the second drive and tried to run the original browser from the initial drive, it would default to the same set of folders and files on the second partition because it is now the default drive by virtual of being booted to.  

You could do it if you could run two operating systems at once, side by side, where they can share space on a single monitor or each have its own set of monitor(s) to display on.  Sounds like using VM, right?  Not quite.  Trying to get a host to share one or more monitors with a client is difficult, what with having to individually size and position the window each uses, but the mouse and keyboard only deal with one OS at a time.  You have to manually toggle these between applications using the mouse (I think you can also use Ctrl+Tab, but I will have to check on that).

This means regardless of where the mouse is positioned, you would have to keep mental track of which side had the focus and was active, able to accept keyboard input. Right now the mouse can hover or move about with no effect on where the focus is.  You have to press a mouse button to cause the focus to move to the application that the mouse is positioned over.   You might need the focus to keep up with where the mouse pointer is, so that your eye only has to see the mouse to know where the focus currently is.

This is not a good idea, because a moving mouse and a shifting focus would drastically effect the ability of the application, the one you are trying to work with,   would keep losing data from the keyboard as you type.   It is only while it has the focus that keyboard input is routed to it.  So constantly shifting focus by having to worry about where the cursor arrow is positioned would be a total nightmare, which is why the mouse presently only gets control when one of its buttons is pressed.  I mean you might need another way to rapidly and visually direct and see where the focus is in order to get around this, but that would only be one more device to manage.

Maybe some easy keyboard combination like using the Scroll Lock key to toggle the mouse between its normal mode and being able to drag the focus with it?  That might work.  I don't know anything offhand that relies on Scroll Lock for any meaningful purpose.  It's almost the key that was never there. But it is, on every keyboard I've encountered.  So maybe a backup key combo in case somebody finds a keyboard without one, or need a Scroll Lock in one application or another.  What's Pause/Break used for?

As far as I know, that is how matters stand.  Too bad our software is not taking advantage of the benefit of our cpu's maybe having multiple cores, so that we can run separate OSes at the same time and have any two (or 4) sharing screen space and be self-toggling as we move the mouse about.  Right now, the chief advantage in running two browsers at the same time is dealing with the frustration of having to wait on one site to finish doing its thing, because you can then use the other browser to deal with a different site or a separate account at the same site in the time that would be wasted otherwise.  A big down side is that running two browsers at once automatically loads your system down, so there are going to be performance gaps at your end to sit through.

You need a fast PC and at least 8 GB of memory (RAM), plus a fast internet connection to not take a big hit on your end sometimes.  And you could have multople intgernet connections, like both a wire and wireless going at once, and your present OS setup is only going to take advantage of one of those, usually the wired connection over the wireless because it is faster.  If you are stuck with dial-up access,  this is not for you.  This is getting into the big leagues.  .

It's noteworthy that we don't even have automatic fallback to wireless if our wired connection is dropped (cable comes loose, or you need to take your connected laptop to another room).  I mean I felt sure it was working in 14.04 at one point, but not here lately.  I searched the internet, and found a script file that removes then reinstalls the wireless driver in order not to have to restart my PC.  So I havea link to it ready to go on my Desktop just in case.

There may not be a fix in the works or anything already out there, but I figure a little talk and exchange of ideas might help for the future.  Any comments or suggestions?

---

### Post by Dennis N on 2015-06-01
> ...This works, but it has to be two separate browsers, _not the same one twice_, because with one browser (even if you add in a tab splitter), your fundamental problem is that you are just using one set of folders and files, and you have to share the same set of cookies and other data as a consequence. You need to have each instance of the browser picked to work in a separate set of folders so that the files do not intermingle.

It can be the same browser twice. You can create multiple _profiles_ for Firefox that keep _separate_ accounts of bookmarks, plugins, addons, history, cookies. You can have two or more instances of Firefox running simultaneously with different profiles.

What you need to do is learn about profiles. Here are a couple of references with more information:

Create and use profiles:
[https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)
Multiple profiles:
[https://developer.mozilla.org/en-US/docs/Mozilla/Multiple_Firefox_Profiles](https://developer.mozilla.org/en-US/docs/Mozilla/Multiple_Firefox_Profiles)

Note: These are from a quick Google search and seem relevant. I have not searched or previewed a lot of links to find the "best". There is information in these for Windows and for Linux. You can certainly learn more by searching Mozilla support. I leave that to you.

---

### Post by deadflowr on 2015-06-01
+1 to separate profiles.

But if you wanted to run two completely, totally separate browsers, try setting up containers.
Primer on gui apps in containers
[https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/)
Probably good to read through container setups in general
[https://www.stgraber.org/2013/12/20/lxc-1-0-your-first-ubuntu-container/](https://www.stgraber.org/2013/12/20/lxc-1-0-your-first-ubuntu-container/)

---

### Post by oldefoxx on 2015-06-01
Profiling may be a way to go, but I realized I have another problem:  I get emails that want to pass me links that call up the default browser, but I am taling for different accounts here, and I've been teying to work a solution where the given account calls up a different browser.

Either I have to do a copy-and-paste of the link lication (okay, address) and put it into the browser of my choosing  manually, or I have to keep changing which browser is the default before I deal with the email thar is in the other account.  Seemsd like there ought to be a profile setting in Thunderbird associating a specific browser with each email account.  I looked around Thunderbirs, and I don't see much resembling a profile except adding and naming new folders and writing some message filter rules.

Oh, you can add more email accounts, but there all you do is name them, enter a password to get to the server, and set parameters for the internet protocol to use.

Were this Windows, I imagine alternate email client software would abound.  But that is not a reason I wouds use to switch back to Windows.  I left Windows  in spite of the fact that the email client software I was then using was not available for Linux.   I am referring to IncrediMail,  It has lots of features I like, although under the huud it is not secure and getting into someone else's email is surprisingly easy.  And you have to edit the Registry to get rid of old accounts, because only a person with the user password can delete his (or her, or anyone;s) account.  But it is stiil nice, free software, which for the Windows world is not the norm.

Checking online, I so-far have found this short list of possible Linux email clients:

Thunderbird  --  Declared Top of the List in one report
Evolution      --  More features than Thunderbird, but a bit unstable and prone to crashes
Kmail            --  feature rich, complex, and really hard to configure.  Okay for 1 account.
Geary           --  Simple, limited features, early stages of development.
Trojita           --  Early development, meant for KDE desktop, limited to just 1 account
Sylpheed     --  Small, simple, fast, but boring to look at when it comes to email contents.
Gmail        --  Just use your web browser
WebMail      --  Something your ISP might provide
Outlook.com  --  Do Outlook via your browser
AOL Mail     --  Another webmail service
Yahoo Mail   --  Yahoo also offers a WebMail service.
Mail.com     --  Sounds plain, but it's more than that
HotMail.com  --  Now redirected to Outlook.com

This link does a comparison of some of the WebMail services. [http://www.digitaltrends.com/web/best-web-based-email-clients/](http://www.digitaltrends.com/web/best-web-based-email-clients/)

The issue with web-based email service is that in most cases, while it's free, you have to deal with setting up new accounts on their servers and not only moving existing emails over, but getting the word of where you are now out to everybody that touches base with you by email,  The simplest solution is to use WebMail (your browser, not an email client) that is set up on your present email provider's server.  

for instance, my ISP is providing my email server, so I can get my email anywhere in the world and using any browser if I go to a Cox Communications site and log in.   To find the site I need, I only have to use Google and search on terms like cox webmail login.  I get several links, and at least one of them will do the trick.

If that does not work for you, there are two different approaches that can come into play:  One is called Reroute or Forward, and are is the same thing:  You write a message rule for each email client on your PC and just send it to your new email address.  But this has the disadvantage that you will be needlessly accumulating excessive messages in two places:  On your PC and with your WebMail provider.  It amy also delay you mail a bit, particularly is your PC is shut down or the email xlient is not running.

The other method involves getting the existing email provider to do Reroute or Relay the messages coming in for you.  They might do that, but this may be something that they don't do.  Here is a link that discusses that approach further:  [https://help.salesforce.com/HTViewHelpDoc?id=email_relay.htm](https://help.salesforce.com/HTViewHelpDoc?id=email_relay.htm)

The main problem with moving away from an email client over to the web browser with WebMail is automatic settings.  Getting to your email periodically, and getting screen notifications if new mail arrives.  And you have to be connected to the internet to read your email, because it is not automatically downloaded to your PC.  You have to weigh these pros and cons out yourself.   These features are what you get with an email client application.

---

