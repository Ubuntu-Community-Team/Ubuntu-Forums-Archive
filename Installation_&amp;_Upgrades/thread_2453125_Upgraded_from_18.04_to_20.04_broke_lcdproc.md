---
title: "Upgraded from 18.04 to 20.04 broke lcdproc"
date: 2020-11-03
forum: Installation &amp; Upgrades
---

### Post by mtbdrew on 2020-11-03
Did the upgrade and everything went well except that now my lcdimon display no longer works at boot. Tried removing and re-installing lcdproc but didn't help. After each reboot have to run "sudo /etc/init.d/LCDd restart" to get display working.

After each reboot status shows:

systemctl status LCDd.service 

&#9679; LCDd.service - LCD display daemon
     Loaded: loaded (/lib/systemd/system/LCDd.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Tue 2020-11-03 07:32:45 CST; 2h 16min ago
       Docs: man:LCDd(8)
             [http://www.lcdproc.org/](http://www.lcdproc.org/)
    Process: 684 ExecStart=/usr/sbin/LCDd -s 1 -f -c /etc/LCDd.conf (code=exited, status=1/FAILURE)
   Main PID: 684 (code=exited, status=1/FAILURE)

Nov 03 07:32:45 frontend LCDd[684]: along with this program; if not, write to the Free Software Foundation,
Nov 03 07:32:45 frontend LCDd[684]: Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
Nov 03 07:32:45 frontend LCDd[684]: imonlcd: ERROR opening /dev/lcd-imon (No such file or directory).
Nov 03 07:32:45 frontend LCDd[684]: imonlcd: Did you load the iMON kernel module?
Nov 03 07:32:45 frontend LCDd[684]: Driver [imonlcd] init failed, return code -1
Nov 03 07:32:45 frontend LCDd[684]: Could not load driver imonlcd
Nov 03 07:32:45 frontend LCDd[684]: There is no output driver
Nov 03 07:32:45 frontend LCDd[684]: Critical error while initializing, abort.
Nov 03 07:32:45 frontend systemd[1]: LCDd.service: Main process exited, code=exited, status=1/FAILURE
Nov 03 07:32:45 frontend systemd[1]: LCDd.service: Failed with result 'exit-code'.

The after the sudo /etc/init.d/LCDd restart:

sudo /etc/init.d/LCDd restart
[sudo] password for frontend: 
Restarting LCDd (via systemctl): LCDd.service.
frontend@frontend:~$ systemctl status LCDd.service 
&#9679; LCDd.service - LCD display daemon
     Loaded: loaded (/lib/systemd/system/LCDd.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 09:55:10 CST; 5s ago
       Docs: man:LCDd(8)
             [http://www.lcdproc.org/](http://www.lcdproc.org/)
   Main PID: 6382 (LCDd)
      Tasks: 1 (limit: 9320)
     Memory: 348.0K
     CGroup: /system.slice/LCDd.service
             &#9492;&#9472;6382 /usr/sbin/LCDd -s 1 -f -c /etc/LCDd.conf

Nov 03 09:55:10 frontend LCDd[6382]: modify it under the terms of the GNU General Public License
Nov 03 09:55:10 frontend LCDd[6382]: as published by the Free Software Foundation; either version 2
Nov 03 09:55:10 frontend LCDd[6382]: of the License, or (at your option) any later version.
Nov 03 09:55:10 frontend LCDd[6382]: This program is distributed in the hope that it will be useful,
Nov 03 09:55:10 frontend LCDd[6382]: but WITHOUT ANY WARRANTY; without even the implied warranty of
Nov 03 09:55:10 frontend LCDd[6382]: MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
Nov 03 09:55:10 frontend LCDd[6382]: GNU General Public License for more details.
Nov 03 09:55:10 frontend LCDd[6382]: You should have received a copy of the GNU General Public License
Nov 03 09:55:10 frontend LCDd[6382]: along with this program; if not, write to the Free Software Foundation,
Nov 03 09:55:10 frontend LCDd[6382]: Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.

I've run "sudo cme edit lcdproc" and checked for any warning or bug messages but there are no issues shown.

Thanks for your help
Andrew

---

### Post by mtbdrew on 2020-11-04
Forgot to mention, in 16.04 and 18.04 I had to run this command "sudo systemctl enable LCDd.service" one time after installing lcdproc in order to get the service to run at boot. Unfortunately this does not make any difference with 20.04.

---

### Post by mtbdrew on 2020-11-11
Anyone?

---

