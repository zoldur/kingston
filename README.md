# Kingston
Shell script to install a [Kingston Masternode](https://www.kingston.cash/) on a Linux server running Ubuntu 16.04. Use it on your own risk.

***
## Installation:
```
wget -q https://raw.githubusercontent.com/zoldur/kingston/master/kingston_install.sh
bash kingston_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the **Kingston Coin Desktop Wallet**.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **5000** **KGX** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is un
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
masternode start-alias MN1
```
***

## Usage:
```
kingston-cli mnsync status
kingston-cli getinfo
kingston-cli masternode status #This command will show your masternode status
```
Also, if you want to check/start/stop **kingston** , run one of the following commands as **root**:

```
systemctl status kingston #To check the service is running.
systemctl start kingston #To start kingston service.
systemctl stop kingston #To stop kingston service.
systemctl is-enabled kingston #To check whetether kingston service is enabled on boot or not.
```
***

## Issues
If your Kingston desktop wallet doesn't sync, go to **Tools -> Open Wallet Configuration File** and add the following entries:
```
addnode=103.19.211.58:9211
addnode=113.212.115.58:9211
addnode=198.98.57.10:9211
addnode=31.53.18.69:9211
addnode=37.187.140.168:9211
addnode=45.64.254.42:9211
addnode=45.64.254.58:9211
addnode=54.36.5.66:9211
addnode=81.169.179.241:9211
```
***

## Wallet resync
If you need to reindex your wallet, run the following commands
```
systemctl stop Kingston
rm -r /root/.kingston/{budget.dat,db.log,fee_estimates.dat,blocks,chainstate,mncache.dat,mnpayments.dat,peers.dat}
systemctl start kingston
```
***

## Donations:  

Any donation is highly appreciated.  

**KGX**: KcaUMDgmTP36ihHidrZr1SVBd2SAdTqr19  
**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh  
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E  
**LTC**: LeZmPXHuQEhkd8iZY7a2zVAwF7DCWir2FF
