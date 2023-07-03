<p align="center">
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/6e674c40-00db-4eb0-83ea-ce4f2d4f84fb" alt="DNS"/>
</p>

<h1>Building Intuition for DNS</h1>
In this project, we will observe A-Record, CNAME Records, and Local DNS Cache <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022

<h2>List of Prerequisites</h2>

- Active Directory lab done
- Client and Domain Controller Connected

<h2>Actions and Observations</h2>

<p>
Connect/log into SC-1 as your domain admin account. For me, it is mydomain.com\jane_admin. Then connect to Client-1 as the admin. 
</p>

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/9b07dfff-77a4-4477-b1f1-82c448dc2e51" height="80%" width="80%" alt="Step 1"/>
</p>
<p>
From Client-1, ping mainframe and notice how it fails.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/2eeea674-9b07-4245-be25-929188a1f9cc" height="80%" width="80%" alt="Step 2"/>
</p>
<p>
Go to DC-1 VM and then to Server Manager. Click Tools then DNS and you should see something like the photo above.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/2cb75b64-ef3a-4052-8bd8-681030654bff" height="80%" width="80%" alt="Step 3"/>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/f49c94ce-9b3e-429c-abf2-402cf50464cb" height="80%" width="80%" alt="Step 4"/>
</p>
<p>
Go to Forward Lookup Zone the mydomain.com. Now we are going to add an A Record called mainframe. Mainframe is going to have the same IP address as dc-1 does.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/13d66679-fb63-4cba-a9d3-af3407f4796e" height="80%" width="80%" alt="Step 5"/>
</p>
<p>
Go back to Client-1 and try to ping mainframe again. This time it should work.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/651b6966-7bac-48fe-87fa-c7e8a97ee5a2" height="80%" width="80%" alt="Step 6"/>
</p>
<p>
Go back to DC-1 and change mainframe's IP address to 8.8.8.8
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/5028b3d5-1f5b-478b-a424-9dfe851e7f81" height="80%" width="80%" alt="Step 7"/>
</p>
<p>
Go back to Client-1 and ping mainframe again. Observe that it still pings the old address because it is stored in the cache.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/d2c1a76f-f691-4655-a68e-7f9fcc85b711" height="80%" width="80%" alt="Step 8"/>
</p>
<p>
Now we are going to flush the dns by using the command ipconfig /flushdns. And the ping mainframe again and it should show the new IP address of 8.8.8.8
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/fff49b1d-a9e0-45d3-b330-6ee568c2fb5a" height="80%" width="80%" alt="Step 9"/>
</p>
<p>
Go to DC-1 and create a CNAME record that points the host "search" to www.google.com. Return to Client-1 and try to ping "search'. 
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/dns-intuition/assets/94804621/a9d1d3d4-5291-42e6-a4b9-738fcae8f174" height="80%" width="80%" alt="Step 10"/>
</p>
<p>
It should be able to ping "search"! This is the end of this project!
</p>
<br />
