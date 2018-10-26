# LinuxTree
Linux技术研究

![](https://i.imgur.com/r2yYlGJ.png)

Linux整体架构

![](https://i.imgur.com/H96FwUm.png)

<pre>
1. Process Scheduler 进程管理，进程调度，负责管理CPU资源，以便让各个进程可以以尽量公平的 方式访问CPU
2. Memory Manager 内存管理，负责管理内存资源，以便让各个进程可以安全地共享机器的内存资源， 另外，内存管理会提供虚拟内存的机制，该机制可以让进程使用多于Memory的内存，
不用的数据通过文件系统保存在外部非易失存储器中，需要使用的时候，再取回到内存中。
3.VFS 虚拟文件系统，Linux内核将不同功能的外部设备，例如DISK设备，输入输出设备，显示设备                    等，抽象为可以通过统一的文件操作接口（open, close, read, write）来访问，这就是Linux一切皆是文件的体现
5.NetWork 网络子系统，负责管理系统的网络设备，并实现各种各样的网络标准
6.IPC 进程间通信，IPC不管理任务的硬件，它主要负责Linux系统间进程之间的通信
</pre>

![](https://i.imgur.com/pVkhSPb.png)

<pre>
bin（binaries）存放二进制可执行文件
sbin(super user binaries) 存放二进制可执行文件，只有root才能访问
etc(etcetera)存放系统配置文件
usr(unix shared resources)用于存放系统的共享资源
home 存放用户文件的根目录
root 超级用户目录
dev(devices)用于存放设备文件
lib(library)存放跟文件系统中的程序运行锁需要的共享库和内核模块
mnt(mount)系统管理员安装零时文件系统的安装点
boot 存放用于系统引导时使用的各种文件
tmp(temporary)用于存放各种零时文件
var(variable)用于存放运行时需要改变数据的文件	
</pre>


Linux下6大IPC机制

<pre>
Linux下进程间通信IPC的集中主要手段
1）管道及有名管道 Pipe, named Pipe
2）信号 Signal
3) 消息队列  Message
5) 共享内存 
6) 信号量 Semaphore
7) Socket 套接字
</pre>

内核空间VS用户空间

![](https://i.imgur.com/mAJNK6g.png)

<pre>
Linux系统只有两层
    高优先级模式（特权模式），低优先级模式（普通模式）
	Linux在高优先级模式中运行系统内核代码以及与硬件相关的代码。
	       低优先级运行营运程序与硬件部分无关部分。
	应用程序不能直接操控硬件或者调用内核函数，需要借助一系列接口函数申请让系统调用相关的代码在内核空间运行 
</pre>

<pre>
Linux系统中每个进程占有4G空间（虚拟空间，并不一定占用）
空间分布如下：
    用户空间： 0~(3G - 1) 普通的应用程序代码运行在此部分空间
    内核空间:  3G~(4G - 1) 内核代码段，其中驱动就运行在此部分空间	
</pre>