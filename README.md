# Ganesh Moulding CRM - Flutter Full Stack App

A comprehensive Flutter CRM application for managing parties and orders for Ganesh Moulding.

## Features

- **Party Management**: Add, view, update, and delete party information
- **Order Tracking**: Create and manage orders for each party
- **Payment Tracking**: Record and track payments for orders
- **Real-time Sync**: Live data synchronization using Supabase
- **Offline Support**: (Coming soon)

## Project Structure

```
lib/
  ├── main.dart                 # App entry point
  ├── screens/
  │   ├── party_list_screen.dart   # List of all parties
  │   ├── party_detail_screen.dart # Individual party details
  │   └── add_party_screen.dart    # Add new party form
  ├── models/
  │   ├── party_model.dart         # Party data model
  │   ├── order_model.dart         # Order data model
  │   └── payment_model.dart       # Payment data model
  └── services/
      └── supabase_service.dart    # Supabase API calls
```

## Getting Started

### Prerequisites

- Flutter 3.0.0 or higher
- Dart SDK
- Supabase account

### Setup Instructions

1. **Clone the Repository**
   ```bash
   cd ganesh_moulding_pati
   ```

2. **Install Dependencies**
   ```bash
   flutter pub get
   ```

3. **Configure Supabase**
   - Create a Supabase project at https://supabase.com
   - Go to Project Settings → API
   - Copy your Supabase URL and Anon Key
   - Create a `.env` file in the project root (copy from `.env.example`):
   ```bash
   # .env
   SUPABASE_URL=your_supabase_project_url
   SUPABASE_ANON_KEY=your_supabase_anon_key
   ```
   
   > **Note**: The `.env` file is gitignored and will not be committed to version control.

4. **Setup Database**
   - Open your Supabase project dashboard
   - Navigate to SQL Editor
   - Run the SQL schema from `database_schema.sql`
   - This will create the required tables (parties, orders, payments) with indexes and RLS policies

5. **Run the App**
   ```bash
   flutter run
   ```

## API Integration

### Supabase Tables

- **parties**: Stores customer/party information
- **orders**: Tracks orders placed by parties
- **payments**: Records payment information for orders

## Dependencies

- `supabase_flutter`: ^1.10.0 - Backend and real-time database
- `flutter_dotenv`: ^5.1.0 - Environment variable management
- `provider`: ^6.0.0 - State management (for future use)
- `intl`: ^0.19.0 - Internationalization
- `uuid`: ^4.0.0 - Unique ID generation

## Future Features

- Order management and tracking
- Payment history and invoicing
- Analytics dashboard
- Mobile app notifications
- Offline data sync
- Multi-user support with authentication

## Development Notes

### Real-time Updates

The app uses Supabase's streaming API to provide real-time updates:
```dart
_partiesStream = Supabase.instance.client
    .from('parties')
    .stream(primaryKey: ['id']);
```

### Error Handling

All database operations include comprehensive error handling and user feedback.

## License

This project is proprietary software for Ganesh Moulding.

## Support

For issues or feature requests, please contact the development team.
