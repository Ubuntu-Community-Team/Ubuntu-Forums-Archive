---
title: "No add computer screen in Lucid B1"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by whollycow on 2010-04-06
I'm running Lucid Netbook Beta 1 and just tried to sync my Ubuntu One account.  The first time I ran the client, the add computer screen came up just fine.  For various reasons, I didn't sync my account at that time and instead closed the browser.

Now when I open the client and click "manage account", it brings up my browser to sign in to my U1 account, but there is no dialog to add my computer.  My U1 account shows that no computers are linked to my account and client preferences doesn't show any synced account.  I don't see an Ubuntu One password entry in my keyring and I've tried deleting ~/.config/ubuntuone and ~/.cache/ubuntuone but that doesn't help.

What can I do to reset my client configuration and sync my computer?

---

### Post by whollycow on 2010-04-06
Update: I just ran
```
u1sync --authorize
```
and I was able to add my computer to my account.  However, the client configuration seems to be unaware of this.  The output in the terminal indicates that authentication failed:
```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 251, in dataReceived
    why = self.lineReceived(line)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1573, in lineReceived
    self.allContentReceived()
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1641, in allContentReceived
    req.requestReceived(command, path, version)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 807, in requestReceived
    self.process()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 125, in process
    self.render(resrc)
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 132, in render
    body = resrc.render(self)
  File "/usr/lib/python2.6/dist-packages/twisted/web/resource.py", line 210, in render
    return m(request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 466, in render_GET
    self.retrieve_function(store=self.store_yes_no, verifier=verifier)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 396, in retrieve_access_token
    access_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 261, in make_token_request
    self._forward_error_callback(error)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
exceptions.Exception: Invalid request token: 2pbdQjkFn0MgqMMLd90R
Authentication failed: TRY_AGAIN

```
I know there have been previous issues with authentication, but I was under the impression that they had been fixed.  I'm running Lucid so everything should be up to date.  Can someone point me in the right direction?

---

### Post by joshuahoover on 2010-04-07
> **whollycow said:**
> Update: I just ran
```
u1sync --authorize
```and I was able to add my computer to my account.  However, the client configuration seems to be unaware of this.  The output in the terminal indicates that authentication failed:
```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/protocols/basic.py", line 251, in dataReceived
    why = self.lineReceived(line)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1573, in lineReceived
    self.allContentReceived()
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 1641, in allContentReceived
    req.requestReceived(command, path, version)
  File "/usr/lib/python2.6/dist-packages/twisted/web/http.py", line 807, in requestReceived
    self.process()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 125, in process
    self.render(resrc)
  File "/usr/lib/python2.6/dist-packages/twisted/web/server.py", line 132, in render
    body = resrc.render(self)
  File "/usr/lib/python2.6/dist-packages/twisted/web/resource.py", line 210, in render
    return m(request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 466, in render_GET
    self.retrieve_function(store=self.store_yes_no, verifier=verifier)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 396, in retrieve_access_token
    access_token = self.make_token_request(oauth_request)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 261, in make_token_request
    self._forward_error_callback(error)
  File "/usr/lib/python2.6/dist-packages/ubuntuone/oauthdesktop/auth.py", line 160, in _forward_error_callback
    raise error
exceptions.Exception: Invalid request token: 2pbdQjkFn0MgqMMLd90R
Authentication failed: TRY_AGAIN

```I know there have been previous issues with authentication, but I was under the impression that they had been fixed.  I'm running Lucid so everything should be up to date.  Can someone point me in the right direction?

Have you tried deleting your Ubuntu One token in the keyring? You can do this via Applications->Accessories->Passwords and Encryption Keys under the "Passwords: default" list. Once you do that, you should run the following via the command line:

killall ubuntuone-syncdaemon ubuntuone-login
ubuntuone-preferences

This should stop the syncdaemon from running and launch the Ubuntu One Preferences which should then prompt to you to add your computer to your account again. After this happens, you should be authenticated. Click on the "Devices" tab in the Preferences window and then click the "Connect" button.

Thank you,

Joshua

---

### Post by whollycow on 2010-04-07
> **joshuahoover said:**
> Have you tried deleting your Ubuntu One token in the keyring? You can do this via Applications->Accessories->Passwords and Encryption Keys under the "Passwords: default" list. Once you do that, you should run the following via the command line:

killall ubuntuone-syncdaemon ubuntuone-login
ubuntuone-preferences

This should stop the syncdaemon from running and launch the Ubuntu One Preferences which should then prompt to you to add your computer to your account again. After this happens, you should be authenticated. Click on the "Devices" tab in the Preferences window and then click the "Connect" button.

Thank you,

Joshua

That worked.  Thanks!

---

### Post by joshuahoover on 2010-04-08
> **whollycow said:**
> That worked.  Thanks!

Great to hear! Sorry for the trouble this caused you. We're still getting some fixes in prior to the final launch of 10.04 LTS. I and the others on the Ubuntu One team greatly appreciate your patience and support!

Thanks!

Joshua

---

### Post by bclintbe on 2010-04-10
I just installed Beta 2 last night, and I can't get my computer to connect now. There is no Ubuntu One token in the keyring for me to delete. In Ubuntu One Preferences the Device tab shows me as <LOCAL MACHINE> and when I click Connect nothing happens. I did sign in to Ubuntu One and delete the name this computer used to have before I installed Beta 2. Any suggestions?

---

### Post by joshuahoover on 2010-04-12
> **bclintbe said:**
> I just installed Beta 2 last night, and I can't get my computer to connect now. There is no Ubuntu One token in the keyring for me to delete. In Ubuntu One Preferences the Device tab shows me as <LOCAL MACHINE> and when I click Connect nothing happens. I did sign in to Ubuntu One and delete the name this computer used to have before I installed Beta 2. Any suggestions?

I'm sorry to hear it's not working properly for you. I'm assuming your network connection is working on this PC. If so, you might want to close Ubuntu One Preferences and then try opening it from the command line and see if any errors are output: ubuntuone-preferences 

If that doesn't provide any information, then you'll likely need to file a bug or hop on #ubuntuone on Freenode IRC. I'm there as joshuahoover most days from 13:00-21:00 UTC. To file a bug, please be sure to attach any log files in your ~/.cache/ubuntuone/log folder to the bug report which you can file here: [https://bugs.edge.launchpad.net/ubuntuone-client/+filebug](https://bugs.edge.launchpad.net/ubuntuone-client/+filebug)

Thank you,

Joshua

---

### Post by bryceowen on 2010-04-28
Just wanted to throw in my two cents. I had the same problem and Joshua's solution fixed it. What I believe initiated the problem was the very first time I clicked Ubuntu One after installing and updating 10.04, Firefox opened two tabs to ubuntuone.com, both asking for my login. When I tried to log into the first tab (I believe the 'authorize computer' page) the site threw me an error complaining about multiple login attempts or something. (I didn't think to copy it at the time, assuming everything would 'just work' when I tried to launch the client again. Alas, not.)

---

