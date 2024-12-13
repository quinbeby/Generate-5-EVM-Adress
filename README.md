1. Install Library yang Diperlukan
Pastikan Anda menginstal library Python berikut terlebih dahulu:

  pip install eth-account

3. Buat File Python
   
nano generate_evm_wallets.py

3. Salin Script Berikut ke File
Salin kode Python di bawah ini ke file generate_evm_wallets.py:

# Required libraries
try:
    from eth_account import Account
    import json
except ImportError:
    print("Installing required libraries...")
    import os
    os.system("pip install eth-account")
    from eth_account import Account
    import json

# Function to generate an EVM wallet
def generate_evm_wallet():
    account = Account.create()
    return {
        "address": account.address,
        "private_key": account.key.hex()
    }

# Generate 5 EVM wallets
evm_wallets = []
for _ in range(5):
    evm_wallets.append(generate_evm_wallet())

# Save wallets to a JSON file
with open("wallets.json", "w") as file:
    json.dump(evm_wallets, file, indent=4)

print("EVM Wallets have been successfully generated and saved in 'wallets.json'.")

4. Jalankan Script
Jalankan script menggunakan Python 3:

python3 generate_evm_wallets.py

5. Cek Hasil
Untuk melihat isi file yang sudah dibuat:

cat wallets.json

6. (Opsional) Unduh File
Jika Anda ingin mengunduh file ke komputer lokal, gunakan SCP:

scp root@<IP-ADDRESS>:/root/wallets.json .


Ganti <IP-ADDRESS> dengan IP VPS Anda.

