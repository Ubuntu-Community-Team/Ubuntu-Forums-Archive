---
title: "Can't open FireFox via VNC"
date: 2018-09-24
forum: Installation &amp; Upgrades
---

### Post by distortedecho on 2018-09-24
Hi

From time to time I like to VNC on to my Ubuntu Server (ubuntu-desktop installed) to do things remotely via a GUI.
I need to open FireFox, but it doesn't launch.

Can anybody help guide me through getting this working again, please?

I've tried Chromium and that also doesn't launch.

---

### Post by ubfan1 on 2018-09-24
Some additional information would be useful to make suggestions.  Is X even running on the server (might be Wayland?)  How do you invoke the vnc server?  What do you see with the vnc viewer? If you launch Firefox from a terminal, do you get any error messages?

---

### Post by SeijiSensei on 2018-09-24
Ubuntu Server by default has no graphical interface.  On systems with GUIs, you can use the "ssh -X hostname" command to set up an encrypted tunnel using the X-Windows protocols.  If you connect to a machine with X or one of its offspring installed, you can run a program from the command prompt, e.g. "firefox &", and it will display on the SSH client's desktop instead of the server's.

---

### Post by ubfan1 on 2018-09-24
Can you display any X program, like xclock?  my vnc start command over ssh, mapping the remote port 5900 to the local port 5900 is:
ssh -t -L 5900:localhost:5900 192.168.1.xxx "sudo x11vnc -localhost -create -auth /var/run/lightdm/root/:0 -display :0"
which works whether or not there's a login active on the remote end.  No auth needed if you already have an X display running there.
I just use xtightvncviewer to start a window with the remote desktop, and allows the gui to start things like the browser, (but I don't have firefox on the remote system).
xtightvncviewer -encodings copyrect -bgr233 localhost::5900

---

### Post by SeijiSensei on 2018-09-24
> **ubfan1 said:**
> Can you display any X program, like xclock?
I believe so, yes.

---

### Post by ubfan1 on 2018-09-24
@senijisensei I should have tagged the question for the OP -- trying to figure out if the problem is with any X program, or just browsers (ram issue?. If the whole desktop is not needed with vnc, the ssh -X is a better way for running just one program, if only for performance.

---

### Post by TheFu on 2018-09-24
> **ubfan1 said:**
> @senijisensei I should have tagged the question for the OP -- trying to figure out if the problem is with any X program, or just browsers (ram issue?. If the whole desktop is not needed with vnc, the ssh -X is a better way for running just one program, if only for performance.

ssh -X is better for LAN connections, not WAN connections.  GUI programs with a large number of XObjects, like a modern browser, will also be slower due to the way that X-events and X-messages are propagated.

VNC+ssh/openvpn or using any of the NX solutions is usually much better than remote X over WAN connections, especially for home users with limited upstream bandwidth.

IME.

---

### Post by distortedecho on 2018-09-26
Thanks for your replies all.

So initially, after upgrading to 18.04, when I VNC'd on to the server, I was greeted with a grey background. Mouse courser was a black X, and the top panel had "Applications" and "Places".
I've since installed lxde an
I could open stuff like gedit, Files. I tried to install TeamViewer, which wouldn't open - and Chromium, which also wouldn't open.

When I start tightvncserver, I do so via SSH with sudo.
This is the error I get when I try to run Firefox via command:

root: Running Firefox as root in a regular user's session is not supported.

su myusername: Client is not authorised to connect to ServerUnable to init server: Could not connect: Connection refused. Error: Cannot open display: :3.0

(vnc is currently connected on :3)

I'm also having curl issues with RSS - but not sure if this is related to this issue?

---

