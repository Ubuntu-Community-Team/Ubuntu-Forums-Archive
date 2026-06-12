---
title: "Failed to read systemd units : Id=smartcard.target | After upgrade 16.04 to 18.04"
date: 2020-11-22
forum: Installation &amp; Upgrades
---

### Post by ubuntobossi on 2020-11-22
I have updated my VPS from 16.04 to 18.04 and get this error message inside Virtualmin below ", when I run "Re-Check Configuration":

**.. your system is ready for use by Virtualmin.**

```
Failed to read systemd units : Id=smartcard.target Names=smartcard.target Conflicts=shutdown.target Before=shutdown.target Documentation=man:systemd.special(7) Description=Smart Card LoadState=loaded ActiveState=inactive SubState=dead FragmentPath=/lib/systemd/system/smartcard.target UnitFileState=static UnitFilePreset=enabled StateChangeTimestampMonotonic=0 InactiveExitTimestampMonotonic=0 ActiveEnterTimestampMonotonic=0 ActiveExitTimestampMonotonic=0 InactiveEnterTimestampMonotonic=0 CanStart=yes CanStop=yes CanReload=no CanIsolate=no StopWhenUnneeded=yes RefuseManualStart=no RefuseManualStop=no AllowIsolate=no DefaultDependencies=yes OnFailureJobMode=replace IgnoreOnIsolate=no NeedDaemonReload=no JobTimeoutUSec=infinity JobRunningTimeoutUSec=infinity JobTimeoutAction=none ConditionResult=no AssertResult=no ConditionTimestampMonotonic=0 AssertTimestampMonotonic=0 Transient=no Perpetual=no StartLimitIntervalUSec=10s StartLimitBurst=5 StartLimitAction=none FailureAction=none SuccessAction=none CollectMode=inactive Type=forking Restart=no NotifyAccess=none RestartUSec=100ms TimeoutStartUSec=1min 30s TimeoutStopUSec=1min 30s RuntimeMaxUSec=infinity WatchdogUSec=0 WatchdogTimestampMonotonic=0 PermissionsStartOnly=no RootDirectoryStartOnly=no RemainAfterExit=no GuessMainPID=yes MainPID=0 ControlPID=0 FileDescriptorStoreMax=0 NFileDescriptorStore=0 StatusErrno=0 Result=success UID=[not set] GID=[not set] NRestarts=0 ExecMainStartTimestampMonotonic=0 ExecMainExitTimestampMonotonic=0 ExecMainPID=0 ExecMainCode=0 ExecMainStatus=0 ExecStart={ path=/usr/share/quota/quotarpc.sh ; argv[]=/usr/share/quota/quotarpc.sh ; ignore_errors=no ; start_time=[n/a] ; stop_time=[n/a] ; pid=0 ; code=(null) ; status=0/0 } Slice=system.slice MemoryCurrent=[not set] CPUUsageNSec=[not set] TasksCurrent=[not set] IPIngressBytes=18446744073709551615 IPIngressPackets=18446744073709551615 IPEgressBytes=18446744073709551615 IPEgressPackets=18446744073709551615 Delegate=no CPUAccounting=no CPUWeight=[not set] StartupCPUWeight=[not set] CPUShares=[not set] StartupCPUShares=[not set] CPUQuotaPerSecUSec=infinity IOAccounting=no IOWeight=[not set] StartupIOWeight=[not set] BlockIOAccounting=no BlockIOWeight=[not set] StartupBlockIOWeight=[not set] MemoryAccounting=no MemoryLow=0 MemoryHigh=infinity MemoryMax=infinity MemorySwapMax=infinity MemoryLimit=infinity DevicePolicy=auto TasksAccounting=yes TasksMax=1149 IPAccounting=no UMask=0022 LimitCPU=infinity LimitCPUSoft=infinity LimitFSIZE=infinity LimitFSIZESoft=infinity LimitDATA=infinity LimitDATASoft=infinity LimitSTACK=infinity LimitSTACKSoft=8388608 LimitCORE=infinity LimitCORESoft=0 LimitRSS=infinity LimitRSSSoft=infinity LimitNOFILE=4096 LimitNOFILESoft=1024 LimitAS=infinity LimitASSoft=infinity LimitNPROC=3830 LimitNPROCSoft=3830 LimitMEMLOCK=67108864 LimitMEMLOCKSoft=67108864 LimitLOCKS=infinity LimitLOCKSSoft=infinity LimitSIGPENDING=3830 LimitSIGPENDINGSoft=3830 LimitMSGQUEUE=819200 LimitMSGQUEUESoft=819200 LimitNICE=0 LimitNICESoft=0 LimitRTPRIO=0 LimitRTPRIOSoft=0 LimitRTTIME=infinity LimitRTTIMESoft=infinity OOMScoreAdjust=0 Nice=0 IOSchedulingClass=0 IOSchedulingPriority=0 CPUSchedulingPolicy=0 CPUSchedulingPriority=0 TimerSlackNSec=50000 CPUSchedulingResetOnFork=no NonBlocking=no StandardInput=null StandardInputData= StandardOutput=journal StandardError=inherit TTYReset=no TTYVHangup=no TTYVTDisallocate=no SyslogPriority=30 SyslogLevelPrefix=yes SyslogLevel=6 SyslogFacility=3 LogLevelMax=-1 SecureBits=0 

```

How can I fix this? The server seems to run normal.

---

